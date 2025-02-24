# Gateway Api

**Only needed for TKGm**

This capability should be used as a workaround in TKGm environments. This is needed becuase the default k8s gateway capability is setup to work with TKGs, which includes the gateway apis by default. TKGm has some of the TKG apis but does not install the gateway apis and this causes the package to get confused and it will install and then uninstall the gatewy apis continously. This package will ensure that the gateway apis are installed so that the oootb package functions as if it is TKGs.  