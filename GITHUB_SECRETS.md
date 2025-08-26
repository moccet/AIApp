# GitHub Secrets Configuration

## How to Add Secrets to GitHub

1. Go to your repository: https://github.com/moccet/AIApp
2. Click **Settings** tab
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click **New repository secret** for each secret below

## Required Secrets

### App Store Connect API (You have these ✅)
- **Secret name**: `APPSTORE_ISSUER_ID`
  - **Value**: `be92a836-9a53-4692-a2db-1b56e5ca57e7`

- **Secret name**: `APPSTORE_KEY_ID`
  - **Value**: `FA8ZKP5GJM`

- **Secret name**: `APPSTORE_PRIVATE_KEY`
  - **Value**: (Paste the entire contents of your AuthKey_FA8ZKP5GJM.p8 file, including the BEGIN and END lines)
  ```
  -----BEGIN PRIVATE KEY-----
  [Your key content here]
  -----END PRIVATE KEY-----
  ```

### Distribution Certificate (Need to create)
- **Secret name**: `CERTIFICATES_P12`
  - **Value**: Run this command after exporting your certificate:
  ```bash
  base64 -i certificates.p12 | pbcopy
  ```
  Then paste the result

- **Secret name**: `CERTIFICATES_P12_PASSWORD`
  - **Value**: The password you set when exporting the certificate

### Fastlane Credentials (Need your Apple ID)
- **Secret name**: `FASTLANE_USER`
  - **Value**: Your Apple ID email

- **Secret name**: `FASTLANE_PASSWORD`
  - **Value**: Your Apple ID password

- **Secret name**: `FASTLANE_APP_SPECIFIC_PASSWORD`
  - **Value**: Generate at https://appleid.apple.com/account/manage
  - Sign in → Security → App-Specific Passwords → Generate

- **Secret name**: `MATCH_PASSWORD`
  - **Value**: Create a strong password for certificate encryption (save this!)

## Next Steps

1. **Download your .p8 file** if you haven't already (you can only download once!)
2. **Export your distribution certificate** from Keychain Access
3. **Generate app-specific password** for your Apple ID
4. **Add all secrets** to GitHub repository

## Security Notes
- Never commit these values to your repository
- Keep your .p8 file backed up securely
- The certificate password should be strong and saved in a password manager