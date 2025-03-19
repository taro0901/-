local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/jensonhirst/Orion/main/source')))()
local Window = OrionLib:MakeWindow({Name = "Title of the library", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})
local Main = Window:MakeTab({
	Name = "Main",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})
Main:AddButton({
	Name = "ESP",
	Callback = function()
 local Players = game:GetService("Players")
local RunService = game:GetService("RunService")

-- ฟังก์ชันสร้าง ESP Box
local function createESP(player)
    player.CharacterAdded:Connect(function(character)
        -- ตรวจสอบว่ามี HumanoidRootPart หรือไม่
        local hrp = character:FindFirstChild("HumanoidRootPart")
        if hrp then
            local box = Instance.new("BoxHandleAdornment")
            box.Size = Vector3.new(4, 6, 4) -- ขนาดของกล่อง
            box.Adornee = hrp
            box.Color3 = Color3.fromRGB(255, 0, 0) -- สีแดง
            box.AlwaysOnTop = true -- ให้กล่องแสดงตลอดเวลา
            box.ZIndex = 10
            box.Transparency = 0.5
            box.Parent = game.CoreGui
        end
    end)
end

-- เพิ่ม ESP ให้ผู้เล่นที่เข้าใหม่
Players.PlayerAdded:Connect(createESP)

-- เพิ่ม ESP ให้ผู้เล่นที่อยู่แล้ว
for _, player in pairs(Players:GetPlayers()) do
    if player ~= Players.LocalPlayer then
        createESP(player)
    end
end

  	end    
})
