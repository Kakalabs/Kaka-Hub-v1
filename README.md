-- Carrega a biblioteca de interface do usuário
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Cria a janela principal
local Window = Library.CreateLib("Kaka Hub", "DarkTheme")

-- Aba Principal
local MainTab = Window:NewTab("Principal")
local MainSection = MainTab:NewSection("Bem-vindo ao Kaka Hub!")

-- Aba de Casas
local HousesTab = Window:NewTab("Casas")
local HousesSection = HousesTab:NewSection("Gerenciamento de Casas")

-- Botão para remover banimento de casas
HousesSection:NewButton("Desbanir de Casa", "Remove o banimento da casa especificada.", function()
    -- Código para remover banimento
    game.ReplicatedStorage.BannedLots:Destroy()
end)

-- Botão para obter permissão de casa
HousesSection:NewButton("Obter Permissão de Casa", "Obtém permissão para a casa especificada.", function()
    -- Código para obter permissão
    -- Substitua 'HouseNumber' pelo número da casa desejada
    local HouseNumber = 1 -- Exemplo
    local args = {
        [1] = "Roommate",
        [2] = HouseNumber
    }
    game:GetService("ReplicatedStorage").Events.Request:FireServer(unpack(args))
end)

-- Aba de Comandos
local CommandsTab = Window:NewTab("Comandos")
local CommandsSection = CommandsTab:NewSection("Comandos Administrativos")

-- Botão para carregar o Infinite Yield
CommandsSection:NewButton("Carregar Infinite Yield", "Carrega o Infinite Yield para comandos adicionais.", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
end)
