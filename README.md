-- Kaka Hub v1 - Script para Brookhaven RP no Executor Delta
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Criando a Janela Principal
local Window = Library.CreateLib("Kaka Hub v1", "DarkTheme")

-- Criando as Abas
local HomeTab = Window:NewTab("Início")
local HouseTab = Window:NewTab("Casas")
local CommandsTab = Window:NewTab("Comandos")
local AvatarTab = Window:NewTab("Avatar")

-- Variáveis globais
local selectedHouse = ""

-- Seção de Início
local HomeSection = HomeTab:NewSection("Bem-vindo ao Kaka Hub")
HomeSection:NewLabel("Discord: https://discord.gg/AQSbuqVt")

-- Aba de Casas
local HouseSection = HouseTab:NewSection("Gerenciamento de Casas")
HouseSection:NewTextBox("Número da Casa", "Digite o número da casa", function(houseNumber)
    selectedHouse = houseNumber
    print("Casa selecionada: " .. selectedHouse)
end)

HouseSection:NewButton("Pegar Permissão", "Pega permissão da casa selecionada", function()
    if selectedHouse ~= "" then
        print("Pegando permissão da casa: " .. selectedHouse)
        -- Adicione aqui o código real para pegar permissão
    else
        print("Por favor, insira um número de casa primeiro.")
    end
end)

HouseSection:NewButton("Remover Banimento", "Remove o banimento da casa selecionada", function()
    if selectedHouse ~= "" then
        print("Removendo banimento da casa: " .. selectedHouse)
        -- Adicione aqui o código real para remover o banimento
    else
        print("Por favor, insira um número de casa primeiro.")
    end
end)

-- Aba de Comandos
local CommandsSection = CommandsTab:NewSection("Comandos")

CommandsSection:NewButton("Infinite Yield", "Executa Infinite Yield", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))()
end)

CommandsSection:NewButton("Fly v3", "Ativa o Fly v3", function()
    local flyScript = [[
        loadstring(game:HttpGet("https://pastebin.com/raw/CaCqj3nX"))()
    ]]
    loadstring(flyScript)()
end)

CommandsSection:NewButton("TP Tool", "Ativa a TP Tool", function()
    local tpToolScript = [[
        loadstring(game:HttpGet("https://pastebin.com/raw/jb74fX1K"))()
    ]]
    loadstring(tpToolScript)()
end)

-- Aba de Avatar
local AvatarSection = AvatarTab:NewSection("Avatar")

AvatarSection:NewButton("Abrir Catálogo", "Abre o catálogo de avatares do Roblox", function()
    game:GetService("Players").LocalPlayer:Kick("Catálogo não pode ser aberto diretamente, use a loja de avatares do Roblox.")
end)

print("Kaka Hub carregado com sucesso!")
