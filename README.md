-- Kaka Hub v1 - Script para Brookhaven RP no Executor Delta local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Criando a Janela Principal local Window = Library.CreateLib("Kaka Hub v1", "DarkTheme")

-- Criando as Abas local HomeTab = Window:NewTab("Início") local HouseTab = Window:NewTab("Casas") local CommandsTab = Window:NewTab("Comandos") local AvatarTab = Window:NewTab("Avatar")

-- Seções das Abas local HomeSection = HomeTab:NewSection("Bem-vindo ao Kaka Hub") HomeSection:NewLabel("Discord: https://discord.gg/AQSbuqVt")

-- Aba de Casas local HouseSection = HouseTab:NewSection("Gerenciamento de Casas") HouseSection:NewTextBox("Número da Casa", "Digite o número da casa", function(houseNumber) selectedHouse = houseNumber end) HouseSection:NewButton("Pegar Permissão", "Pega permissão da casa selecionada", function() print("Pegando permissão da casa: " .. selectedHouse) end) HouseSection:NewButton("Remover Banimento", "Remove o banimento da casa selecionada", function() print("Removendo banimento da casa: " .. selectedHouse) end)

-- Aba de Comandos local CommandsSection = CommandsTab:NewSection("Comandos") CommandsSection:NewButton("Infinite Yield", "Executa Infinite Yield", function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end) CommandsSection:NewButton("Fly v3", "Ativa o Fly v3", function() print("Ativando Fly v3") end) CommandsSection:NewButton("TP Tool", "Ativa a TP Tool", function() print("Ativando TP Tool") end)

-- Aba de Avatar local AvatarSection = AvatarTab:NewSection("Avatar") AvatarSection:NewButton("Abrir Catálogo", "Abre o catálogo de avatares do Roblox", function() game:GetService("StarterGui"):SetCore("Catalog", true) end)

print("Kaka Hub carregado com sucesso!")

