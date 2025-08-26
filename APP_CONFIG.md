# App Configuration Reference

## App Store Connect Details
- **Bundle ID**: `com.moccet.app`
- **SKU**: `aidoctor-2025`
- **App Name**: AI Doctor (or your preferred name)

## Important IDs to Configure

### Required from Apple Developer Portal:
- [ ] Team ID: `YOUR_TEAM_ID`
- [ ] Distribution Certificate: Created in Certificates section
- [ ] Provisioning Profile: Created for `com.moccet.app`

### Required from App Store Connect:
- [ ] App Store Connect Team ID: Found in App Store Connect
- [ ] App ID: Will be generated after creating app (e.g., 1234567890)

### API Keys for CI/CD:
- [x] Issuer ID: `be92a836-9a53-4692-a2db-1b56e5ca57e7`
- [x] Key ID: `FA8ZKP5GJM`
- [ ] Private Key (.p8 file): Download and save securely (AuthKey_FA8ZKP5GJM.p8)

## Files to Update

Once you have the above information, update these files:

1. **ios/ExportOptions.plist**
   - Replace `YOUR_TEAM_ID` with actual Team ID
   - Replace `YOUR_PROVISIONING_PROFILE_NAME` with profile name

2. **ios/fastlane/Appfile**
   - Replace `your-apple-id@example.com` with your Apple ID
   - Replace `YOUR_APP_STORE_CONNECT_TEAM_ID` with ASC Team ID
   - Replace `YOUR_DEVELOPER_PORTAL_TEAM_ID` with Developer Team ID

3. **codemagic.yaml**
   - Replace `1234567890` with your actual App Store Connect App ID

## GitHub Secrets to Add

Go to GitHub repo → Settings → Secrets → Actions and add:

- `CERTIFICATES_P12`: Base64 encoded distribution certificate
- `CERTIFICATES_P12_PASSWORD`: Certificate password
- `APPSTORE_ISSUER_ID`: From App Store Connect API
- `APPSTORE_KEY_ID`: From App Store Connect API
- `APPSTORE_PRIVATE_KEY`: Content of .p8 file
- `FASTLANE_USER`: Your Apple ID email
- `FASTLANE_PASSWORD`: Your Apple ID password
- `FASTLANE_APP_SPECIFIC_PASSWORD`: Generate at appleid.apple.com
- `MATCH_PASSWORD`: Password for Match certificate encryption

## Quick Commands

### Test locally:
```bash
cd ios
flutter build ios --release
```

### Deploy to TestFlight:
```bash
cd ios
fastlane beta
```

### Deploy to App Store:
```bash
cd ios
fastlane release
```

## App Store Connect Submission Checklist

- [ ] App Information filled
- [ ] Screenshots uploaded (all required sizes)
- [ ] App Description written
- [ ] Keywords added
- [ ] Support URL provided
- [ ] Privacy Policy URL added
- [ ] Age Rating questionnaire completed
- [ ] App Category selected
- [ ] Pricing and Availability configured

## Notes
- Repository: https://github.com/moccet/AIApp
- CI/CD will trigger on push to `main` branch
- Manual approval needed for App Store release