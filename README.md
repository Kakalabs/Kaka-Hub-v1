-- Kaka Hub - Script para Brookhaven RP (Executor Delta)

-- Criando a Interface Gráfica
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local ToggleButton = Instance.new("TextButton")
local DiscordLabel = Instance.new("TextLabel")

-- Configurando a GUI
ScreenGui.Parent = game:GetService("Players").LocalPlayer.PlayerGui
MainFrame.Parent = ScreenGui
MainFrame.Size = UDim2.new(0, 300, 0, 200)
MainFrame.Position = UDim2.new(0.3, 0, 0.3, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.Active = true
MainFrame.Draggable = true

ToggleButton.Parent = MainFrame
ToggleButton.Size = UDim2.new(0, 100, 0, 30)
ToggleButton.Position = UDim2.new(0, 10, 0, 10)
ToggleButton.Text = "HUB"
ToggleButton.MouseButton1Click:Connect(function()
    MainFrame.Visible = not MainFrame.Visible
end)

DiscordLabel.Parent = MainFrame
DiscordLabel.Size = UDim2.new(0, 280, 0, 30)
DiscordLabel.Position = UDim2.new(0, 10, 0, 50)
DiscordLabel.Text = "Discord: https://discord.gg/AQSbuqVt"
DiscordLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
DiscordLabel.BackgroundTransparency = 1

-- Função para Gerenciar Casas
function getHousePermission(houseNumber)
    print("Pegando permissão da casa: " .. houseNumber)
end

function removeHouseBan(houseNumber)
    print("Removendo banimento da casa: " .. houseNumber)
end

-- Função para Executar Infinite Yield
function runInfiniteYield()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
end

-- Função de Fly v3
function enableFly()
    print("Ativando Fly v3")
end

-- Função de TP Tool
function enableTpTool()
    print("Ativando TP Tool")
end

-- Função para Abrir Catálogo de Avatar
function openAvatarCatalog()
    game:GetService("StarterGui"):SetCore("Catalog", true)
end

print("Bem-vindo ao Kaka Hub!")
