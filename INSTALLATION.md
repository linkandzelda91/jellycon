# Installation Guide for JellyCon Fork

This is a forked version of JellyCon maintained by linkandzelda91.

## Method 1: Direct Zip Installation (Recommended)

### Step 1: Download the Addon
1. Go to the [Releases page](https://github.com/linkandzelda91/jellycon/releases)
2. Download the latest `plugin.video.jellycon+py3.zip` file

### Step 2: Install in Kodi
1. Open Kodi
2. Go to **Settings** → **Add-ons**
3. Click **Install from zip file**
   - If you see a warning about unknown sources, you need to enable it:
     - Go to **Settings** → **System** → **Add-ons**
     - Enable **Unknown sources**
     - Confirm the warning message
4. Navigate to where you downloaded the zip file
5. Select `plugin.video.jellycon+py3.zip`
6. Wait for the "Add-on installed" notification

### Step 3: Configure
1. The addon should prompt you for your Jellyfin server details
2. If not, go to **Add-ons** → **Video add-ons** → **JellyCon**
3. Follow the setup wizard

## Kodi Version Compatibility

- **Kodi 19 (Matrix) and later**: Use `plugin.video.jellycon+py3.zip`
- **Kodi 18 (Leia) and earlier**: Use `plugin.video.jellycon+py2.zip` (if available)

## Method 2: Manual Installation (Advanced)

If you want to install directly from source:

```bash
git clone https://github.com/linkandzelda91/jellycon.git
cd jellycon
python3 build.py --version py3
```

Then install the generated `plugin.video.jellycon+py3.zip` file in Kodi as described above.

## Troubleshooting

### "Add-on could not be loaded" error
- Make sure you're using the correct version for your Kodi version
- Check that all dependencies are available (they should install automatically)

### Jellyfin server not detected
- Ensure your Kodi device and Jellyfin server are on the same network
- Try entering the server URL manually (format: `http://your-server-ip:8096`)

### Need Help?
- Open an issue on [GitHub](https://github.com/linkandzelda91/jellycon/issues)

## Updating the Addon

To update to a newer version:
1. Download the new release zip file
2. Install it the same way (it will update the existing installation)

Alternatively, you can uninstall the old version first:
- Go to **Add-ons** → **My add-ons** → **Video add-ons** → **JellyCon**
- Click **Uninstall**
- Then install the new version
