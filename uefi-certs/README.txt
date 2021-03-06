This directory contains known public keys for Linux distributions and from
other parties that sign boot loaders and kernels that should be verifiable
by shim. 

Files come with three extensions. A filename ending in .crt is a
certificate file that can be used by sbverify to verify the authenticity of
a key, as in:

$ sbverify --cert centos.crt grubx64.efi

The .cer and .der filename extensions are equivalent, and are public key
files similar to .crt files, but in a different form. The MokManager
utility expects its input public keys in this form, so these are the files
you would use to add a key to the MOK list maintained by MokManager and
used by shim.

The files in this directory are, in alphabetical order:

- canonical-uefi-ca.crt & canonical-uefi-ca.der -- Canonical's public key,
  matched to the one used to sign Ubuntu boot loaders and kernels.

- centos.crt & centos.cer -- Public keys used to sign CentOS binaries, taken
  from shim-signed-0.9-2.el7.src.rpm. Note that the binary's centos.crt file
  was actually in .cer format, and has been renamed appropriately. The
  centos.crt file included here is transformed from the original file by
  openssl. Tested booting CentOS 7.

- fedora-ca.cer & fedora-ca.crt -- Fedora's public key, matched to the one
  used used to sign Fedora's shim 0.8 binary.

- microsoft-kekca-public.der -- Microsoft's key exchange key (KEK), which
  is present on most UEFI systems with Secure Boot. The purpose of
  Microsoft's KEK is to enable Microsoft tools to update Secure Boot
  variables. There is no reason to add it to your MOK list.

- microsoft-pca-public.der -- A Microsoft public key, matched to the one
  used to sign Microsoft's own boot loader. You might include this key in
  your MOK list if you replace the keys that came with your computer with
  your own key but still want to boot Windows. There's no reason to add it
  to your MOK list if your computer came this key pre-installed and you did
  not replace the default keys.

- microsoft-uefica-public.der -- A Microsoft public key, matched to the one
  Microsoft uses to sign third-party applications and drivers. If you
  remove your default keys, adding this one to your MOK list will enable
  you to launch third-party boot loaders and other tools signed by
  Microsoft. There's no reason to add it to your MOK list if your computer
  came this key pre-installed and you did not replace the default keys.
