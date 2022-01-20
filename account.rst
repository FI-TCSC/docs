
==============
User Accounts
==============

Application
===========

1. Go to page id.tuni.fi
2. Choose "Identity management" → "Manage service entitlements" → "Apply for a new entitlement"
3. Choose correct contract (if many)

.. note:: 
    If you fill application as student also tell Course name and the responsible teacher

4. Scroll down and choose "Linux Servers (LINUX-SERVERS) TCSC HPC Cluster"
5. Fill in necessary information and press "Submit" 

Please note that since your application needs confirmation from your manager (does not apply students),
it may take some time until we get it for approval.

You will get two emails after this

* first one when your application is approved and
* second when your user account is created. In this email is also a request for you to create SSH-keypair

Creating SSH-keypair
====================

New Narvi users should create an password protected SSH public key (ed-25519 or
rsa, minimum key length for RSA 2048 bits), and email the public key (NEVER
send your private key) to TCSC, preferably as attachment. Instructions how to
create the key in Linux and in Windows can be found in the sections below.

So you don't have password at cluster at all. The passphrase of private key is
kind of replacement for ssh-password, as it's needed to be able to use private
key, to access cluster. You can create several keys and add several public keys
to your authorized_keys file or you can copy your private key to several
machines, if you need to access cluster from several machines. If you work on
multiple, random, machines, it might be easier to carry your private key with
e.g. on USB-stick.

Key generation on Linux (openssh)
---------------------------------

The command
.. code-block::

    ssh-keygen -t ed25519 -f ~/.ssh/${USER}_narvi_key

creates a key pair (keyname & keyname.pub) in .ssh-directory. It will ask new
passphrase for your private key.

.. note:: 
    TUNI Linux
    On maintained TUNI Redhat Linux, you need to create ssh-keypair to ~/.ssh
    directory, because only then SELinux context will be correct.

If you have working MTA-configuration you could send public-key us with command:
mailx -a .ssh/${USERNAME}_narvi_key.pub -s "Narvi SSH key (${USER})" tcsc.tau@tuni.fi

Using ssh-key in linux
""""""""""""""""""""""

When using key, which isn't named as default, you'll need to specify the used
key when using it. e.g.
.. code-block::

    ssh -i ${USER}_narvi_key your_tuni_username@narvi.tut.fi (username is NOT email-address)

or you could add it to ~/.ssh/config -file like this:
.. code-block::

    Host narvi*.tut.fi
        IdentityFile    ~/.ssh/${USER}_narvi_key

Key generation on Windows
-------------------------

Putty is the preferred client and should available on TUT-intra -machines by default.

Windows 10 Openssh
""""""""""""""""""

If you want to use Windows 10's "native" openssh, then you should follow
Linux-instructions above 

Putty(gen)
""""""""""

1. Start puttygen.
2. Check from below, that key type is ED25519. (older versions of putty don't have ed25519-keys, so should use e.g. 4096 bit RSA-key)
3. Click Generate and draw some picture to puttygen-window to give it some randomness it needs. (wink)
4. Give passphrase for key twice, and note the location you'll save the key.
5. Select the public key from OpenSSH from box at top and save it to some file e.g. narvi.pub.
6. Mail that *.pub as email attachment to tcsc.tau@tuni.fi with subject like "Narvi SSH Key (yourusername)"
.. note::
    Never send or give your private key to anyone!!!


