# Create a Windows VM in Azure with PowerShell

### Connect to Azure account
:point_right: Connect-AzAccount

### Get available Subscriptions 
:point_right: Get-AzSubscription

### Select one of the subscriptions
:point_right: Select-AzSubscription <subscription id>

### Create a resource group 
:point_right: New-AzResourceGroup -Name myResourceGroup -Location EastUS 
  
### Create a VM
:point_right: 
  ```powershell 
  New-AzVm `
    -ResourceGroupName "myResourceGroup" `
    -Name "myVM" `
    -Location "East US" `
    -VirtualNetworkName "myVnet" `
    -SubnetName "mySubnet" `
    -SecurityGroupName "myNetworkSecurityGroup" `
    -PublicIpAddressName "myPublicIpAddress" `
    -OpenPorts 80,3389
```

### Stop a vm 
:point_right: Stop-AzVm -Name <vm_name> -ResourceGroupName <name>  
  
### Connect to the VM through remote desktop 
:point_right: Get-AzRemoteDesktopFile -ResourceGroupName "MyResourceGroup" -Name "MyVm" -Launch
  
### Save the RDP file for the future use
:point_right: Get-AzRemoteDesktopFile -ResourceGroupName "MyResourceGroup" -Name "MyVm" -LocalPath "C:\Path\to\folder"

### Restart a VM
:point_right: Restart-AzVM -ResourceGroup "myResourceGroup" -Name "myVm"

### Redeploy your VM
:point_right: Set-AzVM -Redeploy -ResourceGroupName "myResourceGroup" -Name "myVm"

### RDP Troubleshoo: How to Verify Network Security Group rules?
- This troubleshooting step verifies that you have a rule in your Network Security Group to permit RDP traffic. 
- The default port for RDP is TCP port **3389**. A rule to permit RDP traffic may not be created automatically when you create your VM.

```powershell  
$rules = Get-AzNetworkSecurityGroup -ResourceGroupName "myResourceGroup" `
    -Name "myNetworkSecurityGroup"
  
$rules.SecurityRules
  
Name                     : default-allow-rdp
Id                       : /subscriptions/guid/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkSecurityGroups/myNetworkSecurityGroup/securityRules/default-allow-rdp
Etag                     : 
ProvisioningState        : Succeeded
Description              : 
Protocol                 : TCP
SourcePortRange          : *
DestinationPortRange     : 3389
SourceAddressPrefix      : *
DestinationAddressPrefix : *
Access                   : Allow
Priority                 : 1000
Direction                : Inbound  
``` 
