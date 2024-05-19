## Spice Up Your Spotify on Arch Linux: A Beginner's Guide to Spicetify (Flatpak Edition)

This guide will help you install and configure Spicetify on your Arch Linux system using the Flatpak version of Spotify. We offer two methods: an experimental installation script and a detailed manual approach.

##  Installation Methods

### 1. Experimental Installation Script

This script automates the Spicetify installation process. Make sure you already installed Spotify on your system from [Flathub](https://flathub.org) **However, please note it's in early testing and may not work perfectly.**

#### Installation Steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/boudywho/spicetify-arch-installation-guide
   ```
2. **Navigate to the directory:**
   ```bash
   cd spicetify-arch-installation-guide
   ```
3. **Make the script executable:**
   ```bash
   chmod +x spicetify.sh
   ```
4. **Run the script:** Make sure to type "y" when it asks you to install marketplace (it's crucial for the script to work)
   ```bash
   ./spicetify.sh
   ```

#### Troubleshooting:

- Ignore any errors during installation.
- Verify if Spotify is customized after the script completes. Look for the marketplace at the top left.
- If you encounter issues, please open an issue on the [repository](https://github.com/boudywho/spicetify-arch-installation-guide) with the full terminal output for assistance.

**Disclaimer:** This script is experimental and provided "as-is." Use it at your own risk. It is designed for Arch Linux and may not be compatible with other distributions. 

### 2. Manual Installation

####  Step 1: Install Curl

```bash
sudo pacman -S curl
```

####  Step 2: Install Spicetify

```bash
curl -fsSL https://raw.githubusercontent.com/spicetify/spicetify-cli/master/install.sh | sh
```

#### Step 3: Locate Spotify's Flatpak Directory

1. Run the following command to find your Flatpak installations:
   ```bash
   flatpak --installations
   ```
2. Look for an entry containing `com.spotify.Client` and note the path to its directory.
3. Navigate through the subfolders until you find one containing files like `spotify`, `xpui`, etc. This is Spotify's installation directory.

   **Example path:** `/var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/`

#### Step 4: Configure Spicetify

1. Open Spicetify's configuration file:
   ```bash
   nano ~/.config/spicetify/config-xpui.ini
   ```
2. Find the line `spotify_path =` and paste the path you found in Step 3. Ensure there are no leading or trailing spaces.
   ![Configuration Screenshot](https://github.com/boudywho/spicetify-arch-installation-guide/assets/113399517/f77ba8a7-872b-4983-afff-a39884e769ba)
3. Save the file (Ctrl+X, then Y, then Enter).

#### Step 5: Locate Spotify's Preferences File

1. Run the following command to find Spotify's preferences file:
   ```bash
   find ~ -name 'prefs' -path '*com.spotify.Client*'
   ```
2. Copy the entire path displayed.

#### Step 6: Configure Spicetify with Preferences Path

1. Open Spicetify's configuration file again:
   ```bash
   nano ~/.config/spicetify/config-xpui.ini 
   ```
2. Find the line `prefs_path =` and paste the path to the preferences file you copied.
   ![Preferences Path Screenshot](https://github.com/boudywho/spicetify-arch-installation-guide/assets/113399517/4f1fa362-c173-4e54-973b-247b080144c0)
3. Save the file.

#### Step 7: Grant Permissions

1. Give Spicetify permission to modify Spotify's files:
   ```bash
   sudo chmod a+wr <Spotify Flatpak folder path> 
   sudo chmod a+wr -R <Spotify Flatpak folder path>/Apps
   ```
   Replace `<Spotify Flatpak folder path>` with the path from Step 3.

#### Step 8: Apply Spicetify

```bash
spicetify backup apply
```

#### Step 9: Install Spicetify Marketplace

```bash
curl -fsSL https://raw.githubusercontent.com/spicetify/spicetify-marketplace/main/resources/install.sh | sh
```

##  Customization

You're all set! Now you can explore Spicetify's features and personalize your Spotify experience.
