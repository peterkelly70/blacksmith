Blacksmith

Blacksmith is a powerful Bash script designed to manage Minecraft mods on your headless Ubuntu server using the CurseForge API. Leveraging the capabilities of GUM for interactive command-line interfaces, Blacksmith provides a streamlined and efficient way to enhance your Minecraft server's gameplay experience without the need for a graphical interface.
Table of Contents

    Features
    Prerequisites
    Installation
    Configuration
    Usage
        Interactive Mode
        Command-Line Mode
        List Installed Mods
    Examples
    Troubleshooting
    Logging
    Contributing
    License
    Acknowledgments

Features

    Install Mods: Easily install Minecraft mods directly from CurseForge by selecting from an interactive menu.
    Remove Mods: Seamlessly remove installed mods using an intuitive interface.
    List Mods: View all currently installed mods on your server.
    Automated Downloads: Automatically fetch the latest version of the specified mod.
    Interactive Menus: Utilize GUM to create user-friendly menus and selections for managing mods.
    Logging: Keep track of all installation and removal actions for auditing purposes.
    Headless Compatibility: Designed specifically for headless Ubuntu servers without a graphical interface.

Prerequisites

Before using Blacksmith, ensure your server meets the following requirements:

    Ubuntu 24.04 Server: Blacksmith is optimized for Ubuntu 24.04. Ensure your server is running this version.
    LGSM (Linux Game Server Manager): Your Minecraft server should be managed via LGSM.
    Java Installed: Minecraft servers require Java. Verify it's installed:

java -version

If not installed:

sudo apt update
sudo apt install default-jdk -y

Curl and JQ Installed: Blacksmith utilizes curl for API requests and jq for JSON parsing.

sudo apt update
sudo apt install -y curl jq

GUM Installed: GUM is used to create interactive command-line interfaces.

    Installation via Homebrew:

brew install gum

Installation via Script:

        bash <(curl -s https://raw.githubusercontent.com/charmbracelet/gum/master/install.sh)

    CurseForge API Key: Obtain an API key from CurseForge to interact with their API.

Installation

    Clone the Blacksmith Repository:

git clone https://github.com/yourusername/blacksmith.git

(Replace yourusername with your actual GitHub username if hosted there.)

Navigate to the Script Directory:

cd blacksmith

Make the Script Executable:

chmod +x blacksmith.sh

Move the Script to a Directory in Your PATH (Optional):

    sudo mv blacksmith.sh /usr/local/bin/blacksmith

    This allows you to run blacksmith from anywhere in the terminal.

Configuration

    Obtain a CurseForge API Key:
        Create a CurseForge Account: If you don't have one, sign up at https://curseforge.com/.
        Apply for an API Key:
            Visit the CurseForge API Key Request Page.
            Log in and request a new API key.
            Note down your API Key; you'll need it for the script.

    Set Up Environment Variables:

    To securely store your API key and define your mods directory, set the following environment variables:

nano ~/.bashrc

Add the following lines at the end of the file:

# CurseForge API Key
export CURSEFORGE_API_KEY="your_curseforge_api_key_here"

# Minecraft Server Mods Directory
export MINECRAFT_MODS_DIR="/path/to/lgsm/mcsserver/serverfiles/mods"

    Replace "your_curseforge_api_key_here" with your actual CurseForge API key.
    Replace "/path/to/lgsm/mcsserver/serverfiles/mods" with the actual path to your Minecraft server's mods directory.

Apply the Changes:

    source ~/.bashrc

Usage

Blacksmith provides both an Interactive Mode and a Command-Line Mode to manage your Minecraft mods.
Interactive Mode

Interactive Mode leverages GUM to present user-friendly menus for managing mods.

    Launch Interactive Mode:

    blacksmith

    Navigate the Menus:
        Install a Mod: Select from a list of available mods fetched from CurseForge.
        Remove a Mod: Choose from your currently installed mods to remove.
        List Mods: View all mods currently installed on your server.

Command-Line Mode

For quick operations, Blacksmith also supports command-line arguments.
Install a Mod

To install a mod, use the install command followed by the mod's name in quotes.

blacksmith install "Mod Name"

Example:

blacksmith install "The Twilight Forest"

Remove a Mod

To remove a mod, use the remove command followed by the mod's name in quotes.

blacksmith remove "Mod Name"

Example:

blacksmith remove "The Twilight Forest"

List Installed Mods

To list all currently installed mods on your server, use the list command.

blacksmith list

Examples

    Installing "Biomes O' Plenty":

blacksmith install "Biomes O' Plenty"

Output:

Searching for mod "Biomes O' Plenty"...
Found mod: Biomes O' Plenty (ID: 12345)
Retrieving latest file download URL...
Download URL: https://media.curseforge.com/.../biomesoplenty.jar
Downloading mod...
Mod "Biomes O' Plenty" has been installed successfully.

Removing "Biomes O' Plenty":

blacksmith remove "Biomes O' Plenty"

Output:

Searching for mod "Biomes O' Plenty"...
Found mod: Biomes O' Plenty (ID: 12345)
Removing mod file: biomesoplenty.jar
Mod "Biomes O' Plenty" has been removed successfully.

Listing Installed Mods:

blacksmith list

Output:

    Installed Mods:
    thetwilightforest.jar
    dungeoncrawl.jar
    biomesoplenty.jar

Troubleshooting
Common Issues

    No Mods Found: Error:

No mods found with the name "Mod Name".

Solution:

    Ensure the mod name is spelled correctly.
    Verify that the mod exists on CurseForge.
    Check your CurseForge API key is correctly set.

Download URL Not Found: Error:

No downloadable files found for mod ID 12345.

Solution:

    The mod may not have a compatible version for your Minecraft or Forge version.
    Verify the mod's available versions on CurseForge.

Permissions Errors: Error:

Permission denied

Solution:

    Ensure you have the necessary permissions to write to the mods directory.
    You might need to run the script with sudo if permissions are restricted:

    sudo blacksmith install "Mod Name"

API Rate Limits Exceeded: Error:

    Error: Rate limit exceeded. Please try again later.

    Solution:
        Wait for a while before making more API requests.
        Implement a delay or retry mechanism in the script for future enhancements.

Logging

Blacksmith logs all installation and removal actions to help you keep track of changes.

    Log File Location:

~/blacksmith.log

Viewing Logs:

cat ~/blacksmith.log

Sample Log Entry:

    2024-04-27 14:22:10 - Installed mod: The Twilight Forest
    2024-04-27 15:05:45 - Removed mod: The Twilight Forest

Contributing

Contributions are welcome! If you have suggestions for improvements or encounter issues, feel free to open an issue or submit a pull request.

    Fork the Repository: Click the "Fork" button at the top right of the repository page.

    Clone Your Fork:

git clone https://github.com/yourusername/blacksmith.git

Create a New Branch:

cd blacksmith
git checkout -b feature/YourFeatureName

Make Your Changes and Commit:

git add .
git commit -m "Add Your Feature"

Push to Your Fork:

    git push origin feature/YourFeatureName

    Submit a Pull Request: Go to your forked repository on GitHub and click "Compare & pull request."

License

Distributed under the MIT License. See LICENSE for more information.
Acknowledgments

    CurseForge API: For providing a robust API to manage Minecraft mods.
    LGSM (Linux Game Server Manager): For simplifying Minecraft server management on Linux.
    GUM: For enabling interactive command-line interfaces.
    Minecraft Modding Community: For creating and maintaining an extensive library of mods that enhance gameplay.
