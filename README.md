# AksReplaceBinaries

This is a framework which can be used by developers to replace Windows networking binaries for continous development and testing. Developers can use this framework to test their custom binaries in a single click. This can be mostlyt used when there is a crashing binary or wanted to replace binary with extended logs.
This also has provision to replace the custom binary with the original one with just a change of a flag.
This can also be used to set or delete reg keys, copy files/scripts to nodes and execute some script inside the node.
The framework brings up a daemonset host process containers in every node and use this pods to copy files between local machine and nodes.

#### Space where binaries to be kept : Dir .\binaries

#### For sfpcopy.exe should also be present in binaries directory.

#### Flags to changed for specific usecases [Inside replacebinaries.ps1]
```
$CreateZip = $true
$CopyBinaries = $true
$KeepOriginal = $false # This will replace the selected binaries with original binaries
$EnableTestSigning = $false
$ReplaceHns = $true
$ReplaceVfpCtrl = $false
$ReplaceVfpExt = $false
$ReplaceVfpApi = $false
$ReplaceKubeProxy = $false
$ReplaceAzureVnet = $false
$ReplaceTcpIpSys = $false
$ReplaceNetioSys = $false
$SetRegKeys = $false
$RunPSScript = $false
```

#### reg Key Commands can be added here:
```
$RegKeys = @(
    "reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\hns\State /v HNSLbNatDupRuleChange /t REG_DWORD /d 1 /f", 
    "reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\VfpExt\Parameters /v VfpIpv6DipsPrintingIsEnabled /t REG_DWORD /d 1 /f"
)
```