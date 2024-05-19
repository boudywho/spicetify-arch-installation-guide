## Spice Up Your Spotify: A Beginner's Guide to Installing Spicetify on Arch Linux (Flatpak Edition)

**Let's get started!**

1. **Install the tool:**

   * **Curl:** For downloading Spicetify.
     ```bash
     sudo pacman -S curl
     ``` 

2. **Get Spicetify (The Easy Way):**

   ```bash
   curl -fsSL https://raw.githubusercontent.com/spicetify/spicetify-cli/master/install.sh | sh
   ```
   This one-liner downloads and installs Spicetify automatically!

3. **Find Spotify's Hideout:**

   * Spotify lives in a hidden folder within your Flatpak installation. To find it, run:
     ```bash
     flatpak --installations
     ```
   * You'll see a path to your Flatpak directory. Look for a folder containing something like `com.spotify.Client`.
   * Keep digging through subfolders until you find one with files like `spotify`, `xpui`, etc. This is where Spotify hides!  
   * For example, on my machine, Spotify's files were located here:  `/var/lib/flatpak/app/com.spotify.Client/x86_64/stable/active/files/extra/share/spotify/`

4. **Tell Spicetify where to look:**

   * Open Spicetify's configuration file with:
     ```bash
     nano ~/.config/spicetify/config-xpui.ini 
     ```
   * Find the line `spotify_path =` and paste the path to the folder you found in step 3.  Make sure there are no spaces or extra characters at the beginning or end of the path.
   * Save the file by pressing Ctrl+X, then Y, then Enter.
   * Should look like this
![image](https://github.com/boudywho/spicetify-arch-installation-guide/assets/113399517/f77ba8a7-872b-4983-afff-a39884e769ba)

5. **Unlock Spotify's Secrets:**

   * Spotify keeps its settings in a preferences file. Let's find it:
     ```bash
     find ~ -name 'prefs' -path '*com.spotify.Client*'
     ```
   * This will show you the path to Spotify's preferences file. Copy the entire path.
   * Open Spicetify's configuration file again:
     ```bash
     nano ~/.config/spicetify/config-xpui.ini 
     ```
   * For example, on my machine, Spotify's files were located here:  `/home/boudy/.var/app/com.spotify.Client/config/spotify/prefs`
   * Find the line `prefs_path =` and paste the path to the preferences file you just copied.
   * Should Look like this
   * ![image](https://github.com/boudywho/spicetify-arch-installation-guide/assets/113399517/4f1fa362-c173-4e54-973b-247b080144c0)

   * Save the file like you did before (Ctrl+X, Y, Enter).

6. **Give Spicetify permission:**

   * We need to allow Spicetify to modify Spotify's files:
     ```bash
     sudo chmod a+wr <Spotify Flatpak folder path> 
     sudo chmod a+wr -R <Spotify Flatpak folder path>/Apps
     ```
     Replace `<Spotify Flatpak folder path>` with the path you found in step 3. 

7. **Spice it Up!**
     ```bash
     spicetify backup apply
     ```

9. **Market-Place:**
   * To get the marketplace, use this command
     ```bash
     curl -fsSL https://raw.githubusercontent.com/spicetify/spicetify-marketplace/main/resources/install.sh | sh
     ```
Now go forth and customize your Spotify experience! 
