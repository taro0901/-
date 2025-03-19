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

-- ฟังก์ชันสร้างป้ายชื่อ
local function createNameTag(player)
    -- รอให้ตัวละครของผู้เล่นโหลด
    player.CharacterAdded:Connect(function(character)
        -- ตรวจสอบว่ามีหัว (Head) หรือไม่
        local head = character:FindFirstChild("Head")
        if head then
            -- สร้าง BillboardGui
            local billboard = Instance.new("BillboardGui")
            billboard.Size = UDim2.new(4, 0, 1, 0) -- ขนาดป้ายชื่อ
            billboard.StudsOffset = Vector3.new(0, 2, 0) -- ระยะห่างจากหัว
            billboard.Adornee = head -- ติดไว้กับหัว
            billboard.Parent = head

            -- สร้าง TextLabel สำหรับชื่อผู้เล่น
            local textLabel = Instance.new("TextLabel")
            textLabel.Size = UDim2.new(1, 0, 1, 0)
            textLabel.BackgroundTransparency = 1 -- โปร่งใส
            textLabel.Text = player.Name -- ใส่ชื่อผู้เล่น
            textLabel.TextColor3 = Color3.fromRGB(255, 255, 255) -- สีขาว
            textLabel.TextStrokeTransparency = 0 -- ขอบตัวอักษร
            textLabel.TextScaled = true -- ปรับขนาดอัตโนมัติ
            textLabel.Font = Enum.Font.GothamBold -- ใช้ฟอนต์สวยๆ
            textLabel.Parent = billboard
        end
    end)
end

-- เพิ่มป้ายชื่อให้ผู้เล่นที่เข้ามาใหม่
Players.PlayerAdded:Connect(createNameTag)

-- เพิ่มป้ายชื่อให้ผู้เล่นที่อยู่ในเกมแล้ว
for _, player in pairs(Players:GetPlayers()) do
    createNameTag(player)
end
  	end    
})
