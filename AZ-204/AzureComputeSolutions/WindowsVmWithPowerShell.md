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

  
  
