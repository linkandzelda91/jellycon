# Publishing Guide for JellyCon Fork

This guide explains how to publish and maintain your JellyCon fork.

## Initial Setup (One-time)

### 1. Verify Your Fork on GitHub
Your fork should already be at: `https://github.com/linkandzelda91/jellycon`

### 2. Commit Your Changes
The template and README have been updated. Commit these changes:

```bash
cd /home/gdewitt/jellycon
git add .
git commit -m "Update fork metadata and add installation guide"
git push origin master
```

## Creating a Release

You have two options:

### Option A: Automated Release (Recommended)

1. **Update the version in `release.yaml`**:
   - Edit the `version` field (e.g., `0.8.3-fork.2`)
   - Update the `changelog` section with your changes

2. **Commit your changes**:
   ```bash
   git add release.yaml
   git commit -m "Bump version to X.X.X"
   git push origin master
   ```

3. **Create and push a tag**:
   ```bash
   git tag v0.8.3-fork.2
   git push origin v0.8.3-fork.2
   ```

4. **The GitHub Action will automatically**:
   - Build both py2 and py3 versions
   - Create a GitHub release
   - Attach the zip files

### Option B: Manual Release

1. **Build locally**:
   ```bash
   cd /home/gdewitt/jellycon
   python3 build.py --version py3
   python3 build.py --version py2
   ```

2. **Go to GitHub**:
   - Visit `https://github.com/linkandzelda91/jellycon/releases`
   - Click "Draft a new release"
   - Create a tag (e.g., `v0.8.3-fork.2`)
   - Upload the generated zip files:
     - `plugin.video.jellycon+py3.zip`
     - `plugin.video.jellycon+py2.zip`
   - Write release notes
   - Click "Publish release"

## Version Numbering Strategy

For your fork, use this format: `ORIGINAL_VERSION-fork.INCREMENT`

Examples:
- `0.8.3-fork.1` - Your first fork release
- `0.8.3-fork.2` - Your second fork release with fixes
- `0.8.4-fork.1` - Based on upstream 0.8.4

This makes it clear it's a fork while tracking the upstream version.

## How Users Will Install Your Fork

Users will:
1. Go to your releases page: `https://github.com/linkandzelda91/jellycon/releases`
2. Download the latest `plugin.video.jellycon+py3.zip`
3. Install it in Kodi via "Install from zip file"

See `INSTALLATION.md` for the full user guide.

## Making Changes to Your Fork

### Regular Development Workflow

1. Make your changes to the code
2. Test locally if possible
3. Update `release.yaml` with new version and changelog
4. Commit and push:
   ```bash
   git add .
   git commit -m "Description of your changes"
   git push origin master
   ```
5. Create a release (see above)

### Syncing with Upstream (Optional)

If you want to pull in updates from the original JellyCon repo:

```bash
# Add the original repo as upstream (one-time)
git remote add upstream https://github.com/jellyfin/jellycon.git

# Fetch upstream changes
git fetch upstream

# Merge upstream changes into your fork
git merge upstream/master

# Resolve any conflicts, then push
git push origin master
```

## Important Files

- **`release.yaml`**: Version and changelog
- **`.config/template.xml`**: Addon metadata (name, description, links)
- **`README.md`**: Main documentation
- **`INSTALLATION.md`**: User installation guide
- **`.github/workflows/release.yaml`**: Automated build and release

## Troubleshooting

### Build fails locally
Make sure you have PyYAML installed:
```bash
pip install pyyaml
```

### GitHub Action fails
- Check that `release.yaml` has valid YAML syntax
- Ensure the tag name starts with `v` (e.g., `v0.8.3-fork.1`)

### Users report installation errors
- Make sure they're using the correct version (py3 for Kodi 19+)
- Check that `addon.xml` was generated correctly during build
- Verify dependencies in `release.yaml` are correct

## Next Steps

1. **Right now**: Commit and push the updated files
2. **Test**: Build locally and test in your own Kodi instance
3. **Publish**: Create your first release (v0.8.3-fork.1)
4. **Share**: Share the release link with users

## Questions?

If you need help:
- GitHub Actions logs: Check `.github/workflows/` runs
- Build issues: Run `python3 build.py --version py3 --dev` for debugging
- Kodi issues: Check Kodi logs at `~/.kodi/temp/kodi.log`
