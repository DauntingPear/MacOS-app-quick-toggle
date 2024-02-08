# App Quick Toggle
A HammerSpoon script to allow quick window hiding and opening from any space
Particularly useful with Yabai

## Installation
HammerSpoon is needed to run this script
Install this script in the `~/.hammerspoon` directory

## Configuration
The script resides in the `init.lua` file, which is the file run by HammerSpoon when loading config.
The script containing the config is `bind_windows.lua`. It returns a lua table containing the bindings.
```lua
-- Example for Kitty terminal
local windows = {
    kitty = {
        modifier = 'option',
        key = 'return',
        bundle_ID = '',
        title = 'kitty',
        manage_size = false,
        -- As manage_size is false, these will not be used
        -- manage_size is most useful when not managing apps with yabai
        frame_properties = {
            width = 100,
            height = 100,
            xPos = 100,
            yPos = 100,
        }
    }
}
```
The bundle ID is automatically filled by using the "title" field to get the bundle ID when the script is run.
This is done by running an osascript command `osascript -e 'id of app 'APP'`. This can be run in a temrinal as well to get the BundleID of a mac app.

There currently is not any error handling for this command so if it breaks it will break. The most common error is HammerSpoon dying and not responding. To fix this, open Activity monitor and force quit the process. This often also results in the app bound to the keybind dying as well. This only ocurs when the hotkey is pressed. Another way it breaks is if the frame_properties of the app sets it to an improper size, such as 0, a decimal/fraction, or a size that is too small. In this case, both hammerspoon and the app will have to be forcefully exited and restarted.
