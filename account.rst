
==============
User Accounts
==============

Application
===========

1. Go to page id.tuni.fi
2. Choose "Identity management" → "Manage service entitlements" → "Apply for a new entitlement"
3.  Choose correct contract (if many)
.. note:: 

	If you fill application as student also tell Course name and the responsible teacher

4. Scroll down and choose "Linux Servers (LINUX-SERVERS) TCSC HPC Cluster"
5. Fill in necessary information and press "Submit" 

Please note that since your application needs confirmation from your manager (does not apply students) it may take some time until we get it for approval.

You will get two emails after this

* first one when your application is approved and
* second when your user account is created. In this email is also a request for you to create SSH-keypair

Creating SSH-keypair
====================

New Narvi users should create an password protected SSH public key (ed-25519 or rsa, minimum key length for RSA 2048 bits), and email the public key (NEVER send your private key) to TCSC, preferably as attachment. Instructions how to create the key in Linux and in Windows can be found in the sections below.

So you don't have password at cluster at all. The passphrase of private key is kind of replacement for ssh-password, as it's needed to be able to use private key, to access cluster. You can create several keys and add several public keys to your authorized_keys file or you can copy your private key to several machines, if you need to access cluster from several machines. If you work on multiple, random, machines, it might be easier to carry your private key with e.g. on USB-stick.
