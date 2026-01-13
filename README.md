# IPA keyboard

International Phonetic Alphabet keyboard layout for desktop Linux distributions

It is possible to add the IPA keyboard layout to the system's keyboard layouts and make it **available** from the **settings** in just a few steps.

🚨 However, mind that dealing with system's files requires `sudo` privileges, so make sure you **know what you are doing**.

## Installation

Keyboard layouts are stored in `/usr/share/X11/xkb/symbols`, so copy the `ipa` file into that directory.

```bash
sudo cp ipa /usr/share/X11/xkb/symbols/
```

Now you must let system know that there is a new keyboard layout file, ready to use. To do so, we must add a few lines to the `/usr/share/X11/xkb/rules/evdev.xml` file. Remember that you must open this file with `sudo` in order to save changes.

```xml
<layout>
  <configItem>
  <name>ipa</name>
  <!-- Keyboard indicator for IPA layouts -->
  <shortDescription>ipa</shortDescription>
  <description>IPA</description>
  <languageList>
    <iso639Id>ipa</iso639Id>
  </languageList>
  </configItem>
</layout>
```

Lines must be added as a child to the `layoutList` element.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xkbConfigRegistry SYSTEM "xkb.dtd">
<xkbConfigRegistry version="1.1">
  <modelList>
    ⋮
  </modelList>
  <layoutList>
    ⋮
    <!-- paste here -->
  </layoutList>
  <optionList>
    ⋮
  </optionList>
</xkbConfigRegistry>
```

## Accessing the layout

Go to: `Settings` ⮕ `Keyboard` ⮕ `Input Sources` and click the `+` button.

Then, a window will pop up, asking you to chose an input source. Click `⋮` ⮕ `Other` and search for the `IPA`.

After the selection, you can switch to the the new keyboard layout using `Super` + `Space` shortcut.

👀 If you would like to check how to access a **particular symbol** on the keyboard, click the layout menu at the top right corner of the screen and click `Show Keyboard Layout`.

🗑️ When everything is alright, you can safely **delete** this repository.

## Troubleshooting

If you cannot access the layout from the settings, perform those steps:

1. Make sure the `ipa` file has read access rights.
2. Check if the `layout` element has been pasted to the `evdev.xml` correctly.
3. Log out and log in.
4. Restart your computer.

## Modification

Feel free to take this layout and modify it to fit your needs.
