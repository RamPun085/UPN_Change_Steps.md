# UPN_Change_Steps.md
# 🔄 Changing UPN in Active Directory  This guide explains how to update a user account's User Principal Name (UPN) and sAMAccountName in Active Directory from:

---

## 🧭 Steps Using Active Directory Users and Computers (ADUC)

1. **Open ADUC**  
   - Go to: `Start > Administrative Tools > Active Directory Users and Computers`

2. **Find the User Account**  
   - Navigate to the appropriate Organizational Unit (OU)
   - Right-click on `ram.pun@magarlegend.com` and select **Properties**

3. **Update the User Logon Name (UPN)**  
   - Go to the **Account** tab
   - Change the **User logon name** to `rpun`
   - Ensure the domain suffix is `@magarlegend.com`

4. **(Optional) Update Pre-Windows 2000 Username (sAMAccountName)**  
   - In the **Account** tab, change the legacy username from `ram.pun` to `rpun` if needed

5. **Click Apply or OK** to save changes

---

## 🛠️ Steps Using PowerShell

```powershell
# Define old and new UPN
$oldUPN = "ram.pun@magarlegend.com"
$newUPN = "rpun@magarlegend.com"

# Get the user
$user = Get-ADUser -Filter {UserPrincipalName -eq $oldUPN}

# Set the new UPN and sAMAccountName
Set-ADUser $user -UserPrincipalName $newUPN -SamAccountName "rpun"
