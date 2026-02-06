# Kavo UI Library
This is a stable release for Kavo UI by XHeptc

## Update

Added:
Mobile Support
BlueTheme

Updated:
SerpentTheme

### Getting the Loader
```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/OnyxIsCool/Kavo/refs/heads/main/KavoUI_Source.lua"))()
```

### Creating an Window
```lua
local Window = Library.CreateLib("TITLE", "DarkTheme")
```

Themes:
LightTheme,
BlueTheme,
DarkTheme,
GrapeTheme,
BloodTheme,
Ocean,
Midnight,
Serpent,
Synapse

### Creating an Tab
```lua
local Tab = Window:NewTab("Tab")
```

### Creating an Section
```lua
local Section = Tab:NewSection("Section")
```

### Creating an Label
```lua
local Label = Section:NewLabel("Label")
```

### Creating an Button
```lua
Section:NewButton("Button", "ButtonText", function()
    -- ...
end)
```

### Creating an Toggle
```lua
Section:NewToggle("Toggle", "ToggleText", function()
    -- ...
end)
```

### Creating an Slider
```lua
Section:NewSlider("Slider", "SliderText", 500, 0, function() -- 500 (MaxValue), 0 (MinValue)
    -- ...
end)
```

### Creating an TextBox
```lua
Section:NewTextBox("Textbox", "TextboxText", function()
	-- ...
end)
```

### Creating an Keybind
```lua
Section:NewKeybind("Keybind", "KeybindText", Enum.KeyCode.E, function()
	-- ...
end)
```

### Creating an Dropdown
```lua
Section:NewDropdown("Dropdown", "DropdownText", {"1", "2", "3"}, function()
    -- ...
end)
```

### Creating an Colorpicker
```lua
Section:NewColorPicker("Colorpicker", "Color Info", Color3.fromRGB(255, 255, 255), function()
    -- ...
end)
```

# Library Functions
```lua
Library:ToggleUI()
```
This minimizes the interface you can also add it to keybinds or buttons

# Elements Functions

### Update Section
```lua
Section:UpdateSection("Section 2")
```

### Update Label
```lua
Label:UpdateLabel("Label Updated!")
```

### Update Button
```lua
Button:UpdateButton("New Text")
```
Make sure your button is local when updating it.

### Update Toggle
```lua
getgenv().Toggled = false

local toggle = Section:NewToggle("Toggle", "Info", (state)
    getgenv().Toggled = state
end)

game:GetService("RunService").RenderStepped:Connect(function()
	if getgenv().Toggled then
		toggle:UpdateToggle("Toggle On")
	else
		toggle:UpdateToggle("Toggle Off")
	end
end)
```

### Dropdown Refresh
```lua
local oldList = {
  "2019",
  "2020"
}
local newList = {
  "2021",
  "2022"
}
local dropdown = Section:NewDropdown("Dropdown","Info", oldList, function()

end)
Section:NewButton("Update Dropdown", "Refreshes Dropdown", function()
  dropdown:Refresh(newList)
end)
```

# Applying Custom Themes / Colors
Make new table, here you are going to put your colors, as shown below.
```lua
local colors = {
    SchemeColor = Color3.fromRGB(0,255,255),
    Background = Color3.fromRGB(0, 0, 0),
    Header = Color3.fromRGB(0, 0, 0),
    TextColor = Color3.fromRGB(255,255,255),
    ElementColor = Color3.fromRGB(20, 20, 20)
} 
```
Applying it: Change your window code little bit.
```lua
local Window = Library.CreateLib("TITLE", colors)
```

## Want to add fully customizable UI?
Add this code in your section. This will create color pickers.

Make sure you have added table with all the values of UI. then apply it to window. Like shown above.
```lua
for theme, color in pairs(themes) do
    Section:NewColorPicker(theme, "Change your "..theme, color, function(color3)
        Library:ChangeColor(theme, color3)
    end)
end
```
