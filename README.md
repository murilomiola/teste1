-- Criar ScreenGui
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criar Frame (HUB)
local HubFrame = Instance.new("Frame")
HubFrame.Size = UDim2.new(0, 200, 0, 120)
HubFrame.Position = UDim2.new(0.05, 0, 0.3, 0)
HubFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
HubFrame.BorderSizePixel = 0
HubFrame.Parent = ScreenGui

-- Criar UI Corner
local UICorner = Instance.new("UICorner")
UICorner.CornerRadius = UDim.new(0, 8)
UICorner.Parent = HubFrame

-- Criar Botão "Marcar Posição"
local BotaoMarcar = Instance.new("TextButton")
BotaoMarcar.Size = UDim2.new(1, -20, 0, 40)
BotaoMarcar.Position = UDim2.new(0, 10, 0, 10)
BotaoMarcar.Text = "Marcar Posição"
BotaoMarcar.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
BotaoMarcar.TextColor3 = Color3.fromRGB(255, 255, 255)
BotaoMarcar.Parent = HubFrame

local UICorner2 = Instance.new("UICorner")
UICorner2.CornerRadius = UDim.new(0, 6)
UICorner2.Parent = BotaoMarcar

-- Criar Botão "Teleportar"
local BotaoTeleportar = Instance.new("TextButton")
BotaoTeleportar.Size = UDim2.new(1, -20, 0, 40)
BotaoTeleportar.Position = UDim2.new(0, 10, 0, 70)
BotaoTeleportar.Text = "Teleportar"
BotaoTeleportar.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
BotaoTeleportar.TextColor3 = Color3.fromRGB(255, 255, 255)
BotaoTeleportar.Parent = HubFrame

local UICorner3 = Instance.new("UICorner")
UICorner3.CornerRadius = UDim.new(0, 6)
UICorner3.Parent = BotaoTeleportar

-- Variável que armazena a posição marcada
local posicaoMarcada = nil

-- Função do botão "Marcar Posição"
BotaoMarcar.MouseButton1Click:Connect(function()
	local char = game.Players.LocalPlayer.Character
	if char and char:FindFirstChild("HumanoidRootPart") then
		posicaoMarcada = char.HumanoidRootPart.Position
		BotaoMarcar.Text = "Posição marcada!"
		wait(1)
		BotaoMarcar.Text = "Marcar Posição"
	end
end)

-- Função do botão "Teleportar"
BotaoTeleportar.MouseButton1Click:Connect(function()
	local char = game.Players.LocalPlayer.Character
	if posicaoMarcada and char and char:FindFirstChild("HumanoidRootPart") then
		char.HumanoidRootPart.CFrame = CFrame.new(posicaoMarcada)
		BotaoTeleportar.Text = "Teleportado!"
		wait(1)
		BotaoTeleportar.Text = "Teleportar"
	else
		BotaoTeleportar.Text = "Nenhuma posição!"
		wait(1)
		BotaoTeleportar.Text = "Teleportar"
	end
end)
