#tiw-menu

Menu System for the QBCore Framework
```lua
RegisterCommand("menutest", function(source, args, raw)
    openMenu({
        {
            header = "Main Title",
            isMenuHeader = true, -- Set to true to make a nonclickable title
        },
        {
            header = "Sub Menu Button",
            txt = "This goes to a sub menu",
            params = {
                event = "tiw-menu:client:testMenu2",
                args = {
                    number = 1,
                }
            }
        },
        {
            header = "Sub Menu Button",
            txt = "This goes to a sub menu",
            disabled = true,
            -- hidden = true, -- doesnt create this at all if set to true
            params = {
                event = "tiw-menu:client:testMenu2",
                args = {
                    number = 1,
                }
            }
        },
    })
end)
```
```lua
RegisterNetEvent('tiw-menu:client:testMenu2', function(data)
    local number = data.number
    openMenu({
        {
            header = "< Go Back",
        },
        {
            header = "Number: "..number,
            txt = "Other",
            params = {
                event = "tiw-menu:client:testButton",
                args = {
                    message = "This was called by clicking this button"
                }
            }
        },
    })
end)
```
```lua
RegisterNetEvent('tiw-menu:client:testButton', function(data)
    QBCore.Functions.Notify(data.message)
end)
