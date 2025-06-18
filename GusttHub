loadstring(game:HttpGet("https://raw.githubusercontent.com/SeuUsuario/GusttHub/main/main.lua"))()

local GusttHub = {}

GusttHub.Settings = {
    AutoUpdate = true,
    AntiBan = true,
    Keybinds = {
        Teleport = "T",
        CopySkin = "C",
        KillPlayer = "V",
        Troll = "B"
    }
}

function GusttHub.Teleport(target)
    local char = game.Players.LocalPlayer.Character
    if char and target.Character then
        char.HumanoidRootPart.CFrame = target.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, 3)
    end
end

function GusttHub.CopySkin(target)
    for _, v in next, target.Character:GetDescendants() do
        if v:IsA("BasePart") then
            game.Players.LocalPlayer.Character[v.Name].Color = v.Color
            if v:FindFirstChildOfClass("Decal") then
                v:FindFirstChildOfClass("Decal"):Clone().Parent = game.Players.LocalPlayer.Character[v.Name]
            end
        end
    end
end

function GusttHub.KillWithCar(target)
    local car = game.Players.LocalPlayer.Character:FindFirstChildOfClass("VehicleSeat")
    if car then
        car.CFrame = target.Character.HumanoidRootPart.CFrame
        car.Velocity = Vector3.new(0, 0, 100)
    end
end

local ScreenGui = Instance.new("ScreenGui", game.CoreGui)
local Frame = Instance.new("Frame", ScreenGui)
Frame.Size = UDim2.new(0.2, 0, 0.3, 0)
Frame.Position = UDim2.new(0.8, 0, 0.5, 0)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 40)

local buttons = {
    {"TP para Jogador", function() GusttHub.Teleport(game.Players:GetPlayers()[2]) end},
    {"Copiar Skin", function() GusttHub.CopySkin(game.Players:GetPlayers()[2]) end},
    {"Eliminar com Carro", function() GusttHub.KillWithCar(game.Players:GetPlayers()[2]) end}
}

for i, btn in ipairs(buttons) do
    local Button = Instance.new("TextButton", Frame)
    Button.Text = btn[1]
    Button.Size = UDim2.new(0.9, 0, 0.2, 0)
    Button.Position = UDim2.new(0.05, 0, 0.05 + (i-1)*0.25, 0)
    Button.MouseButton1Click:Connect(btn[2])
end

game:GetService("UserInputService").InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode[GusttHub.Settings.Keybinds.Teleport] then
        GusttHub.Teleport(game.Players:GetPlayers()[2])
    elseif input.KeyCode == Enum.KeyCode[GusttHub.Settings.Keybinds.CopySkin] then
        GusttHub.CopySkin(game.Players:GetPlayers()[2])
    elseif input.KeyCode == Enum.KeyCode[GusttHub.Settings.Keybinds.KillPlayer] then
        GusttHub.KillWithCar(game.Players:GetPlayers()[2])
    end
end)

game.StarterGui:SetCore("SendNotification", {
    Title = "GUSTT HUB CARREGADO!",
    Text = "Use as teclas T/C/V para funções rápidas",
    Duration = 10
})

return GusttHub
