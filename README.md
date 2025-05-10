local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/kav"))()
local colors = {
    SchemeColor = Color3.fromRGB(0,255,255),
    Background = Color3.fromRGB(0, 0, 0),
    Header = Color3.fromRGB(0, 0, 0),
    TextColor = Color3.fromRGB(255,255,255),
    ElementColor = Color3.fromRGB(20, 20, 20)
}

local Window = Library.CreateLib("Angel Hub", colors)
local Tab = Window:NewTab("Main")
local Section = Tab:NewSection("Controls")

-- Botão
Section:NewButton("Click Me", "Prints Clicked", function()
    print("Clicked")
end)

-- Toggle
getgenv().Toggled = false
Section:NewToggle("Example Toggle", "Toggle Info", function(state)
    getgenv().Toggled = state
    print("Toggle is now:", state)
end)

-- Slider
Section:NewSlider("WalkSpeed", "Changes WalkSpeed", 500, 0, function(s)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

-- TextBox
Section:NewTextBox("Say Something", "Type anything", function(txt)
    print("You typed:", txt)
end)

-- Keybinds
Section:NewKeybind("Print Key", "Prints when pressed", Enum.KeyCode.F, function()
    print("You just clicked the bind")
end)

Section:NewKeybind("Toggle UI", "Toggles the UI", Enum.KeyCode.RightControl, function()
    Library:ToggleUI()
end)

-- Dropdown
local oldList = { "2019", "2020" }
local newList = { "2021", "2022" }
local dropdown = Section:NewDropdown("Years", "Pick a year", oldList, function(option)
    print("Selected:", option)
end)

Section:NewButton("Update Dropdown", "Refreshes Dropdown", function()
    dropdown:Refresh(newList)
end)

-- Color Pickers
for theme, color in pairs(colors) do
    Section:NewColorPicker(theme, "Change your " .. theme, color, function(color3)
        Library:ChangeColor(theme, color3)
    end)
end
