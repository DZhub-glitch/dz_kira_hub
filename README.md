# dz_kira_hub
một script hack roblox tương thích với krnl
-- DZ HUB - From Việt Nam
if not game:IsLoaded() then
    game.Loaded:Wait()
end

-- Anti AFK
local VirtualUser = game:service'VirtualUser'
game:service'Players'.LocalPlayer.Idled:connect(function()
    VirtualUser:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
    wait(1)
    VirtualUser:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
end)

-- UI Lib (đơn giản, custom sau)
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

local Window = Library.CreateLib("DZ HUB | From Việt Nam", "DarkTheme")

-- Language Table (chỉ hiển thị Vietnamese đầu)
local Languages = {
    "Vietnamese", "English", "Japanese", "Korean", "Chinese", "Spanish", "French", "German", "Russian", "Thai", 
    "Portuguese", "Italian", "Indonesian", "Turkish", "Polish", "Arabic", "Hindi", "Hebrew", "Greek", "Dutch"
}

-- Tab: Settings
local Settings = Window:NewTab("⚙️ Settings")
local SectionLang = Settings:NewSection("🌐 Ngôn ngữ")

SectionLang:NewDropdown("Chọn ngôn ngữ", "Chọn ngôn ngữ cho giao diện", Languages, function(currentLang)
    print("Đã chọn ngôn ngữ: " .. currentLang)
end)

-- Tab: Auto Farm
local AutoFarm = Window:NewTab("⚔️ Auto Farm")
local Farm = AutoFarm:NewSection("Farm Titan")
Farm:NewToggle("Auto Farm Titan", "Tự động đánh titan", function(state)
    print("Auto Farm Titan: ", state)
end)

Farm:NewToggle("Auto Tele to Titan", "Tự động teleport tới titan gần nhất", function(state)
    print("Auto Tele: ", state)
end)

-- Tab: Combat
local Combat = Window:NewTab("⚡ Combat")
local CombatSec = Combat:NewSection("Tấn công")
CombatSec:NewToggle("Super Fast Attack", "Tăng tốc đánh", function(state)
    print("Fast Attack: ", state)
end)

CombatSec:NewToggle("Auto Kill Boss Raid", "Chỉ giết Boss", function(state)
    print("Kill Boss Only: ", state)
end)

-- Tab: Utility
local Utility = Window:NewTab("🧰 Utility")
local UtilSec = Utility:NewSection("Tiện ích")
UtilSec:NewToggle("Fly Hack", "Bay né Titan", function(state)
    print("Fly Hack: ", state)
end)

UtilSec:NewToggle("Auto Escape", "Thoát khi bị titan bắt", function(state)
    print("Auto Escape: ", state)
end)

UtilSec:NewToggle("Auto Reload", "Tự thay bình", function(state)
    print("Auto Reload: ", state)
end)

-- Tab: ESP & Safe
local ESP = Window:NewTab("🛰️ ESP / Safe")
local EspSec = ESP:NewSection("Tầm nhìn & an toàn")

EspSec:NewToggle("Titan ESP", "Nhìn thấy titan qua tường", function(state)
    print("Titan ESP: ", state)
end)

EspSec:NewToggle("Player ESP", "Nhìn thấy người chơi", function(state)
    print("Player ESP: ", state)
end)

EspSec:NewToggle("Fail Safe (Admin Check)", "Tắt cheat khi admin vào", function(state)
    print("Fail Safe: ", state)
end)

EspSec:NewToggle("God Mode", "Bất tử", function(state)
    print("God Mode: ", state)
end)

-- Tab: Misc
local Misc = Window:NewTab("🎮 Misc")
local MiscSec = Misc:NewSection("Khác")
MiscSec:NewButton("Auto Retry", "Tự chơi lại sau khi chết hoặc thắng", function()
    print("Retry Called")
end)

MiscSec:NewButton("Auto Open Chest", "Mở rương sau khi raid", function()
    print("Chest Open Called")
end)

MiscSec:NewLabel("Made by: DZ - From Việt Nam 🇻🇳")

-- Auto Load for KRNL
if identifyexecutor and identifyexecutor() == "Krnl" then
    print("DZ HUB đã load trên KRNL thành công!")
end
