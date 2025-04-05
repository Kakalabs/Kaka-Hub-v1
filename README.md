-- Carrega a biblioteca de interface do usuário
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Cria a janela principal
local Window = Library.CreateLib("Kaka Hub v2", "DarkTheme")

-- Mensagem de boas-vindas
local WelcomeScreen = Instance.new("ScreenGui", game.CoreGui)
local WelcomeText = Instance.new("TextLabel", WelcomeScreen)
WelcomeText.Size = UDim2.new(0, 400, 0, 50)
WelcomeText.Position = UDim2.new(0.5, -200, 0.2, 0)
WelcomeText.Text = "Bem-vindo ao Kaka Hub!"
WelcomeText.TextSize = 24
WelcomeText.BackgroundTransparency = 1
WelcomeText.TextColor3 = Color3.new(1, 1, 1)
wait(3)
WelcomeScreen:Destroy()

-- Aba Principal
local MainTab = Window:NewTab("Principal")
local MainSection = MainTab:NewSection("Bem-vindo ao Kaka Hub!")
MainSection:NewLabel("Este script foi criado com base na sua solicitação.")
MainSection:NewLabel("Use com cautela e esteja ciente dos riscos.")

-- Aba de Casas
local HousesTab = Window:NewTab("Casas")
local HousesSection = HousesTab:NewSection("Gerenciamento de Casas")

-- Label informativo
HousesSection:NewLabel("Número da Casa:")

-- Campo de entrada para o número da casa
local HouseNumber = Instance.new("TextBox", HousesSection.MainFrame)
HouseNumber.PlaceholderText = "Digite o número"
HouseNumber.Size = UDim2.new(0.9, 0, 0.15, 0)
HouseNumber.Position = UDim2.new(0.05, 0, 0.2, 0)
HouseNumber.TextSize = 16
HouseNumber.Font = Enum.Font.SourceSans
HouseNumber.Text = "1" -- Valor padrão

-- Função para obter o número da casa
local function getHouseNumber()
    return tonumber(HouseNumber.Text) or 1
end

-- Botão para remover banimento de casas
HousesSection:NewButton("Desbanir de Casa", "Remove o banimento da casa especificada.", function()
    local houseId = getHouseNumber()
    local BannedLots = game:GetService("ReplicatedStorage"):FindFirstChild("BannedLots")
    if BannedLots then
        for i, v in pairs(BannedLots:GetChildren()) do
            if v:IsA("IntValue") and v.Value == houseId then
                v:Destroy()
                break
            end
        end
        game:GetService("Players").LocalPlayer:Chat("Banimento da casa " .. houseId .. " removido (se existir).")
    else
        game:GetService("Players").LocalPlayer:Chat("Não há casas banidas no momento.")
    end
end)

-- Botão para obter permissão de casa (simulação - pode não funcionar devido a proteções do jogo)
HousesSection:NewButton("Obter Permissão de Casa", "Tenta obter permissão para a casa especificada.", function()
    local houseId = getHouseNumber()
    local ReplicatedStorage = game:GetService("ReplicatedStorage")
    local RequestEvent = ReplicatedStorage:FindFirstChild("Events") and ReplicatedStorage.Events:FindFirstChild("Request")
    if RequestEvent then
        RequestEvent:FireServer("Roommate", houseId)
        game:GetService("Players").LocalPlayer:Chat("Solicitação de permissão para a casa " .. houseId .. " enviada.")
    else
        game:GetService("Players").LocalPlayer:Chat("Evento de solicitação não encontrado.")
    end
end)

-- Aba de Gamepasses Grátis
local GamepassTab = Window:NewTab("Gamepasses")
local GamepassSection = GamepassTab:NewSection("Gamepasses Grátis")

GamepassSection:NewLabel("A funcionalidade de gamepasses grátis geralmente não é possível devido às proteções do Roblox.")
GamepassSection:NewLabel("Qualquer botão aqui pode não ter o efeito desejado.")

GamepassSection:NewButton("Pegar Todas Gamepasses (Pode não funcionar)", "Tenta ativar todas as gamepasses do Brookhaven.", function()
    local Player = game:GetService("Players").LocalPlayer
    local Passes = {"Premium", "Music", "VehiclePack", "Estate", "SWAT", "Speed", "Unicorn", "Firefighter", "SpecialForces"}
    for _, pass in pairs(Passes) do
        Player[pass].Value = true -- Tentativa de setar o valor (pode ser read-only)
    end
    game:GetService("Players").LocalPlayer:Chat("Tentativa de ativar todas as gamepasses.")
end)

-- Aba de Avatar
local CatalogTab = Window:NewTab("Avatar")
local CatalogSection = CatalogTab:NewSection("Editar Avatar")

CatalogSection:NewButton("Abrir Editor de Avatar", "Abre a página de edição de avatar do Roblox no navegador.", function()
    game:GetService("GuiService"):OpenBrowserWindow("https://www.roblox.com/my/avatar")
end)
CatalogSection:NewLabel("Equipar itens gratuitos ou já comprados aqui.")
CatalogSection:NewLabel("A compra de itens pagos requer Robux.")

-- Aba de Comandos
local CommandsTab = Window:NewTab("Comandos")
local CommandsSection = CommandsTab:NewSection("Comandos")

CommandsSection:NewButton("Carregar Infinite Yield", "Carrega o Infinite Yield para comandos avançados.", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
end)

CommandsSection:NewButton("Fly V3", "Ativa o modo de voar (versão 3).", function()
    local Player = game:GetService("Players").LocalPlayer
    local Character = Player.Character or Player.CharacterAdded:Wait()
    local HumanoidRootPart = Character:WaitForChild("HumanoidRootPart")
    local Humanoid = Character:WaitForChild("Humanoid")
    local Flying = false

    game:GetService("UserInputService").InputBegan:Connect(function(Input, GPE)
        if not GPE then
            if Input.KeyCode == Enum.KeyCode.F then
                Flying = not Flying
                Humanoid.PlatformStand = Flying
                if Flying then
                    game:GetService("Players").LocalPlayer:Chat("Fly V3 Ativado")
                else
                    game:GetService("Players").LocalPlayer:Chat("Fly V3 Desativado")
                end
            end
        end
    end)

    game:GetService("RunService").Stepped:Connect(function()
        if Flying and Humanoid.Health > 0 then
            HumanoidRootPart.Velocity = Vector3.new(0,0,0)
            HumanoidRootPart.CFrame = HumanoidRootPart.CFrame * CFrame.new(0, -0.5, 0)
        end
    end)
end)

CommandsSection:NewButton("TP Tool", "Ativa uma ferramenta de teleporte.", function()
    local Player = game:GetService("Players").LocalPlayer
    local Mouse = Player:GetMouse()
    local Tool = Instance.new("Tool")
    Tool.Name = "TPTool"

    Tool.Activated:Connect(function
