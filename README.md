# Azure Policy custom samples

In this repo, you can find some custom Azure Policy definitions I've built to govern Azure environments and enforce certain behaviors. 

To deploy any of the Azure Policies from this repo, follow the instructions bellow:

```powershell
# Create the Policy Definition (Subscription scope)
$definition = New-AzPolicyDefinition -Name '<YOUR POLICY NAME>' -DisplayName '<YOUR DISPLAY NAME>' -description '<YOUR POLICY DESCRIPTION>' -Policy '<URL FOR RAW JSON FILE LOCATED IN THIS REPO>' -Parameter '<URL FOR RAW JSON FILE LOCATED IN THIS REPO IN CASE THERE IS ANY>' -Mode All

# Set the scope to a resource group; may also be a subscription or management group
$scope = Get-AzResourceGroup -Name '<YOUR RESOURCE GROUP>'

# Set the Policy Parameter (JSON format)
$policyparam = '{ "<PARAMETER NAME>": "<PARAMETER VALUE>"}'

# Create the Policy Assignment
$assignment = New-AzPolicyAssignment -Name '<POLICY ASSIGNMENT NAME>' -DisplayName '<ASSIGNMENT DISPLAY NAME>' -Scope $scope.ResourceId -PolicyDefinition $definition -PolicyParameter $policyparam
```
