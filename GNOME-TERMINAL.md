# GNOME-TERMINAL
My personal configs are located in the my-terminal-profile.conf file.

## HOW TO EXPORT
1. First find the ID of your profile. This can be found when clicked on your profile in GNOME-terminal. In the tab "Text", bottom right, there is your Profile-ID.
2. Run the following in your terminal WITH YOUR OWN ID:
   ```bash
   PROFILE_ID="12345678-1234-1234-1234-123456789abc"
   ```
4. Afterwards run the following:
   ```bash
   dconf dump /org/gnome/terminal/legacy/profiles:/:$PROFILE_ID/ > my-terminal-profile.conf
   ```
5. Your terminal profile has been exported to your home directory

## HOW TO IMPORT
1. Copy your exported profile config from your own home directory to your target PCs home directory.
2. Run the following in the terminal:
   ```bash
   NEW_ID=$(uuidgen)
   ```
3. Then run:
   ```bash
   dconf load /org/gnome/terminal/legacy/profiles:/:$NEW_ID/ < my-terminal-profile.conf
   ```
4. Then run the following:
   ```bash
   dconf write /org/gnome/terminal/legacy/profiles:/list "$(dconf read /org/gnome/terminal/legacy/profiles:/list | sed "s/]$/, '$NEW_ID']/")"
   ```
Your profile should now appear in your terminal settings.
