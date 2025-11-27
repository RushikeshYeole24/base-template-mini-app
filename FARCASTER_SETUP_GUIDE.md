# Farcaster Mini App Setup Guide

## ✅ Completed Steps

1. **Manifest File Created**: `/public/.well-known/farcaster.json`
   - This file will be accessible at: `https://your-domain.com/.well-known/farcaster.json`
   - Currently configured for: `base-template-mini-app-ubc1.vercel.app`

2. **Vercel Configuration Updated**: Added proper headers for the manifest file

## 📋 Next Steps to Complete Setup

### Step 1: Update Your Domain (If Changed)
If you're using a different domain than `base-template-mini-app-ubc1.vercel.app`, update these fields in `/public/.well-known/farcaster.json`:
- `frame.iconUrl`
- `frame.homeUrl`
- `frame.imageUrl`
- `frame.splashImageUrl`
- `frame.webhookUrl`

### Step 2: Deploy Your App
```bash
npm run deploy:vercel
```
Or deploy through Vercel dashboard.

### Step 3: Verify Manifest is Accessible
After deployment, check that your manifest is live:
```
https://your-domain.com/.well-known/farcaster.json
```

### Step 4: Associate Your Account (If Not Done)
If you need to regenerate the `accountAssociation` fields:

1. **Navigate to Base Build Account Association Tool**
   - URL: https://build.base.org/account-association (or the official tool URL)

2. **Submit Your Domain**
   - Paste your domain: `base-template-mini-app-ubc1.vercel.app` (or your custom domain)
   - Click "Submit"

3. **Sign the Manifest**
   - Click "Verify" button
   - Sign with your wallet
   - This generates the `accountAssociation` fields

4. **Update Manifest with Generated Values**
   - Copy the generated `header`, `payload`, and `signature`
   - Replace the values in `/public/.well-known/farcaster.json`:
   ```json
   "accountAssociation": {
     "header": "YOUR_GENERATED_HEADER",
     "payload": "YOUR_GENERATED_PAYLOAD",
     "signature": "YOUR_GENERATED_SIGNATURE"
   }
   ```

5. **Redeploy**
   - Deploy again to make changes live
   - The platform will re-index your updated configuration

### Step 5: Generate Proper Assets
Use the **Mini App Assets Generator** to create properly formatted:
- Icons (icon.png)
- Splash screens (splash.png)
- Images (image.png)

**Requirements:**
- Icons: Square format, recommended 512x512px
- Splash: Recommended 1200x630px
- Images: Recommended 1200x630px for social sharing

Place generated assets in `/public/` directory.

### Step 6: Update Frame Metadata
Customize these fields in your manifest:
- `name`: Your mini app name
- `subtitle`: Short tagline
- `description`: Detailed description
- `primaryCategory`: Choose from available categories (social, gaming, defi, etc.)
- `splashBackgroundColor`: Hex color for splash screen background

### Step 7: Test Your Mini App
After deployment and reposting:
- Changes take effect when the platform re-indexes
- Test in Farcaster clients
- Verify search and discovery features work
- Check embed rendering

## 📁 File Structure
```
your-project/
├── public/
│   ├── .well-known/
│   │   └── farcaster.json  ← Manifest file
│   ├── icon.png            ← App icon
│   ├── splash.png          ← Splash screen
│   └── image.png           ← Social image (create this)
├── manifest.json           ← Root manifest (keep for reference)
└── vercel.json            ← Updated with headers
```

## 🔍 Verification Checklist
- [ ] Manifest accessible at `/.well-known/farcaster.json`
- [ ] All URLs in manifest point to correct domain
- [ ] Account association fields are valid
- [ ] Assets (icon, splash, image) are properly sized
- [ ] App deployed and live
- [ ] Manifest verified with Base Build tool
- [ ] App reposted to trigger re-indexing

## 🚨 Important Notes
- Changes to manifest require redeployment AND reposting
- The platform re-indexes on repost, not just deployment
- Keep both `manifest.json` (root) and `.well-known/farcaster.json` in sync
- Account association is tied to your wallet and domain

## 🔗 Useful Links
- Base Build Account Association Tool: https://build.base.org/
- Farcaster Documentation: https://docs.farcaster.xyz/
- Mini App Assets Generator: (Use official Farcaster/Base tools)
