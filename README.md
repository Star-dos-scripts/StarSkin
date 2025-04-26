-- Exemplo de botão usando Orion Library
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "Brookhaven Skin", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

local Tab = Window:MakeTab({
	Name = "Roupas",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

Tab:AddButton({
	Name = "Equipar Skin",
	Callback = function()
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()

        for _,v in pairs(character:GetChildren()) do
            if v:IsA("Shirt") or v:IsA("Pants") then
                v:Destroy()
            end
        end

        local shirt = Instance.new("Shirt")
        shirt.ShirtTemplate = "rbxassetid://11856084059"
        shirt.Parent = character

        local pants = Instance.new("Pants")
        pants.PantsTemplate = "rbxassetid://0"
        pants.Parent = character
    end    
})
