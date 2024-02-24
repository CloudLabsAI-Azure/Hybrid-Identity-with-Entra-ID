# Lab 5: Setup MFA and Conditional Access

## Exercise 1: Configure per-user multi-factor authentication

### Task 1: Validate sign-in before enabling MFA

1. On the taskbar, select **Microsoft Edge**.

2. In the address bar, enter **outlook.office.com** and press Enter.
  
3. At the **Sign in** page, enter **<inject key="AzureAdUserEmail"></inject>** and then select **Next**.

4. On the **Enter password** page, enter **<inject key="AzureAdUserPassword"></inject>** and select **Sign in**. At the Edge Save password prompt, select **Save & Turn on**.

5. At the **Stay signed in** prompt, select **No**.

   > Outlook on the Web opens. Take note that only the password was required to sign in to Outlook on the Web.

6. At the top-right corner, select the **Account manager** and then select **Sign out**.

7. Close Microsoft Edge.

### Task 2: Enable MFA for a user

1. On the taskbar select **Microsoft Edge**, in the address bar type **https://entra.microsoft.com**, and then press **Enter**.

2. Sign in as user **<inject key="AzureAdUserEmail"></inject>** and use the tenant Admin password  **<inject key="AzureAdUserPassword"></inject>**. If the **Stay signed in?** prompt appears, select **No**. 

   > The Microsoft Entra admin center opens.

3. At the top of the web page, In the search resources box, type multifactor authentication and then select **multifactor authentication**.

   > The multi-factor authentication page opens.

4. Select **Additional cloud-based multifactor authentication settings**.

5. In the **multi-factor authentication** page, select **service settings**. Select **Allow users to remember multi-factor authentication on devices they trust**.

6. Next to **Number of days users can trust devices for**, enter **30** and then select **save**. 

7. Close the **multi-factor authentication** page.

8. Navigate back to the **Microsoft Entra admin center** Edge tab and in the navigation pane, select **Users** > **All users**.

9. At the top of the user list, select Per-user MFA.

   > The Per-user MFA page opens.

12. In the user list, select the check box next to **Edmund Reeve**.

13. On the **quick steps** pane, select **Enable**.

14. On the **About enabling multi-factor auth** message, select **enable multi-factor auth**.

15. On the **Updates successful** message, select **close**. Take note that the **Multi-Factor Auth Status** for Alex Wilber is now **Enabled**.

16. Close Microsoft Edge.

### Task 3: Register and Validate MFA 

1. On the taskbar, select **Microsoft Edge**.

2. In the address bar, enter **outlook.office.com** and press Enter.

3. On the **Pick an account** page, select **`Edmund Reeve@yourtenant.onmicrosoft.com`**.

4. On the **Enter password** page, enter the tenant password **Pa55-w.rd!** and select **Sign in**.

5. At the **More information required** page, select **Next**. The Keep your account secure page opens.

   > Typically, you will want to use the Microsoft Authenticator app to manage multi-factor authentication. However for this lab scenario, you will use text messages.

6. On the **Keep your account secure** page, select **I want to set up a different method**. Chose **Phone** From the dropdown menu and then click **Confirm**.

7. Enter your mobile phone number which you can receive text messages, and then select **Next**.

8. After you receive the verification code as a text message, enter the code where indicated on the **Keep your account secure** page and then select **Next**.

9. On the **Keep your account secure** page, you will receive a message "Great job! You have successfully set up your security info. Choose **Done** to continue signing in." Select **Done**.

10. At the Stay signed in message, select **No**. 

    > Outlook on the Web opens to Alex Wilber's inbox.

11. At the top-right corner, select the **Account manager forEdmund** and then select **Sign out**.

12. Close Microsoft Edge.

### Task 3: Remove per-user MFA

1. On the taskbar select **Microsoft Edge**, in the address bar type **https://entra.microsoft.com**, and then press **Enter**.

2. Sign in as **<inject key="AzureAdUserEmail"></inject>**, and use the tenant Admin password **<inject key="AzureAdUserPassword"></inject>**, If the **Stay signed in?** prompt appears, select **No**.  

   > The Microsoft Entra admin center opens.

3. In the Microsoft Entra admin center, in the navigation pane, select **Users**.

4. Select **All users** and then at the top of the results pane select **Per-user MFA**. 
   
   > The Per-user MFA page opens.

5. In the user list, select the check box next to **Edmund Reeve**.

6. On the **quick steps** pane, select **Disable**.

7. On the **Disable multi-factor authentication?** message, select **yes**.

8. On the **Updates successful** message, select **close**. Take note that the **Multi-Factor Auth Status** for Edmund Reeve is now **Disabled**.

9. Close Microsoft Edge.

**Results**: After completing this exercise, you will have successfully configured per-user multi-factor authentication.

## Exercise 2: Configure multi-factor authentication using conditional access

### Task 1: Validate sign-in before enabling conditional access with MFA

1. On the taskbar, select **Microsoft Edge**.

2. In the address bar, enter **outlook.office.com** and press Enter.

4. On the **Pick an account** page, select **`Edmund Reeve@yourtenant.onmicrosoft.com`**.

5. On the **Enter password** page, enter the tenant password **Pa55-w.rd!** and select **Sign in**.

6. On the **Stay signed in** page, select **No**. 

   > Outlook opens to Alex's inbox. Take note that only the password was required to sign in to Outlook on the Web as you removed the MFA in the previous Exercise.

7. At the top-right corner, select the **Account manager for Edmund Reeve** and then select **Sign out**.

8. Close Microsoft Edge.

### Task 2: Configure conditional access with MFA

1. On the taskbar select **Microsoft Edge**, in the address bar type **https://entra.microsoft.com**, and then press **Enter**.

2. Sign in as **<inject key="AzureAdUserEmail"></inject>**, and use the tenant Admin password **<inject key="AzureAdUserPassword"></inject>**. If the **Stay signed in?** prompt appears, select **No**. 

   > The Microsoft Entra admin center opens.

3. In the navigation pane, expand **Protection**, and then select **Conditional Access**.

4. On the **Conditional Access** page, select **Policies**, and then select **New policy**.

5. On the **New Conditional access policy** page, in the **Name** box, enter **Contoso MFA Policy**.

6. Under **Assignments**, select **0 users and groups selected**.

7. In the Users and groups pane, select the option next to **Select users and groups** and then select the check box next to **Users and groups**.

8. On the **Select users and groups** page, select **Edmund Reeve** and then select **Select**. 

    > Note that typically you would specify a group, however for this exercise we will just test the setting on Edmund Reeve.

9. Select **No target resources selected** and then click **Select apps**.

    > Note the Control access based on client app setting. This setting allows you to specify the client app that is used to access the resource. For example, you can specify that only the Outlook app can be used to access Exchange Online. 

10. On the **Select** section of the page, click **None**.

11. On the **Select** page, select the check box next to **Office 365** and then click **Select**.

12. Under **Access controls**, in the **Grant** section, select **0 controls selected**.

13. On the **Grant** page, select **Grant access**, select the check box next to **Require multifactor authentication**, and then click **Select**.

14. Under **Enable policy**, select **On**.

15. Select **Create** to create the Contoso MFA Policy. Notice that the policy is listed with a State of **On**.

16. Close Microsoft Edge.

### Task 3: Validate conditional access MFA

1. On the taskbar, select **Microsoft Edge**.

2. In the address bar, enter **https://outlook.office.com** and press Enter.

3. On the **Pick an account** page, select **`Edmund Reeve@yourtenant.onmicrosoft.com`**.

5. On the **Enter password** page, enter the tenant password **Pa55-w.rd!** and select **Sign in**. 

6. At the Verify your identity prompt, select your phone number.

   > The Enter code dialog box opens.

7. At the **Enter code** page, enter the code sent to your mobile phone, and then select **Verify**.

8. At the **Protect your account** page, select **skip for now**.

9. At the Stay signed in message, select **No**. 

   > Outlook on the Web opens to Alex Wilber's inbox.

10. At the top-right corner, select the **Account manager for Edmund Reeve** and then select **Sign out**.

11. Close Microsoft Edge.

### Task 4: Remove conditional access MFA 

1. On the taskbar select **Microsoft Edge**, in the address bar type **https://entra.microsoft.com**, and then press **Enter**.

3. Sign in as user **<inject key="AzureAdUserEmail"></inject>**, and use the tenant Admin password **<inject key="AzureAdUserPassword"></inject>**. If the **Stay signed in?** prompt appears, select **No**. 

   > The Microsoft Entra admin center opens.

4. In the Microsoft Entra admin center, in the navigation pane, expand **Protect & secure** and then select **Conditional Access**.

5. On the **Conditional Access** page, select **Policies** and then select **Contoso MFA Policy**.

6. On the **Contoso MFA Policy** page, select **Delete**.

7. At the **Are you sure?** prompt, select **Yes**.

8. Close Microsoft Edge.

**Results**: After completing this exercise, you will have successfully configured multi-factor authentication by using a conditional access policy.
