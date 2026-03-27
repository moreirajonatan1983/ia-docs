# Authentication Methods

> **Source:** [kiro.dev/docs/getting-started/authentication/](https://kiro.dev/docs/getting-started/authentication/)
> **Page updated:** March 19, 2026

---

Kiro supports the following authentication providers:
- **GitHub**
- **Google**
- **AWS Builder ID**
- **AWS IAM Identity Center**
- **External identity provider** (e.g., Microsoft Entra ID or Okta)

> **Info:** Users that have a paid Kiro subscription and access it through a social login provider (like GitHub or Google) or through AWS Builder ID are considered **individual subscribers**. We may use certain content from Kiro Free Tier and Kiro individual subscribers for service improvement. For more information on service improvement and how to opt out, see [Service improvement](https://kiro.dev/docs/privacy-and-security/).

Kiro is an AWS application that works as a standalone agentic IDE **without needing to set up an AWS account**. You can download and use Kiro immediately without any external account setup — it handles AI interactions and code assistance directly through the application itself.

---

## Available Authentication Methods

### GitHub

Use the following instructions to sign in to Kiro using GitHub.

**To sign in with GitHub:**

1. In Kiro, choose **Sign in with GitHub**. You will be redirected to your default web browser to complete the sign in process.
2. Enter your username or email address and your password and then choose **Sign in**.
3. Choose **Authorize kirodotdev** to authorize the Kiro App with your GitHub account.

---

### Google

Use the following instructions to sign in to Kiro using Google.

**To sign in with Google:**

1. In Kiro, choose **Sign in with Google**. You will be redirected to your default web browser to complete the sign in process.
2. Choose a Google account that you'd like to use with Kiro.
3. Choose **Continue** to authorize the Kiro App with your Google account.

---

### AWS Builder ID

Use the following instructions to sign in to Kiro using AWS Builder ID.

**To sign in with AWS Builder ID:**

1. In Kiro, choose **Login with AWS Builder ID**. You will be redirected to your default web browser to complete the sign in process.
2. Enter your email address and then choose **Next**.
3. Enter your password and then choose **Sign in**.
4. Choose **Allow access** to authorize the Kiro App.

---

### AWS IAM Identity Center

Use the following instructions to sign in to Kiro in your organization — including AWS GovCloud (US) — using AWS IAM Identity Center.

**To sign in with AWS IAM Identity Center:**

1. In Kiro, choose **Sign in with AWS IAM Identity Center**.
2. In **Start URL**, enter the start URL provided by your admin or help desk.
3. In **Region**, enter the AWS Region that hosts the identity directory, and then choose **Continue**.

> **Info:** The authentication methods supported in AWS GovCloud (US) regions are **AWS IAM Identity Center** and **external identity providers**. Individual login methods such as GitHub, Google, and AWS Builder ID are **not available** in AWS GovCloud (US) regions.
>
> Users know they will be using Kiro with AWS GovCloud (US) by ensuring the Start URL used during authentication contains `"us-gov-home"`, for example:
> ```
> https://start.us-gov-home.awsapps.com/directory/d-XXXXXXXXXX
> ```
>
> Kiro uses the same download/installer for both commercial and AWS GovCloud (US) regions. IAM Identity Center authentication automatically routes traffic to the appropriate AWS GovCloud (US) region. **Kiro IDE version 0.9.2+** and **Kiro CLI version 1.25.0+** are required for AWS GovCloud (US) regions support.

---

### External Identity Provider

Use the following instructions to sign in to Kiro using your organization's external identity provider such as Microsoft Entra ID or Okta.

**To sign in with your organization's identity provider:**

1. In Kiro, choose **Your organization**.
2. Enter your work email to find your organization, and then choose **Continue**.
3. Complete the sign-in process with your organization's identity provider.

---

## Troubleshooting Authentication Issues

If you encounter problems during the authentication process, such as browser redirect failures or sign-in errors, check our [troubleshooting guide](https://kiro.dev/docs/troubleshooting/#authentication-issues) for platform-specific solutions and common fixes.

---

## Next Steps

- [Review FAQ →](https://kiro.dev/faq)
- [Explore Agent features →](https://kiro.dev/docs/chat)
- [Get started with Kiro →](https://kiro.dev/docs)