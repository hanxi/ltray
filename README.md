# ltray
System tray icon and menu bind for lua.

# API

```lua
local tray = require "tray"

-- init tray menu
tray.init(tray_conf)

-- update icon or menu items
tray.update(tray_conf)

-- tray event loop
tray.loop()

-- exit tray
tray.exit()
```

# EXAMPLE

```lua
local tray = require "tray"
local tray_conf

local function menu1cb(menuitem)
    menuitem.checked = not menuitem.checked
    tray.update(tray_conf)
end

local function exitcb()
    tray.exit()
end

tray_conf = {
    icon = "",
    menu = {
        {
            text = "menu1",
            cb = menu1cb,    
        },
        {
            text = "quit",
            cb = exitcb,    
        },
    }
}
tray.init(tray_conf)

local function on_cliboard_change(text, from)
    print(text, from)
end

while true do
    if tray.loop() == -1 then
        break
    end
end
```

# BUILD

see `build.bat`

# TODO

Now only support windows. If you want run in Linux or OSX, you can see https://github.com/zserge/tray
