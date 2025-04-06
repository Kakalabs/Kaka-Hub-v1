-- Kaka Hub v2 - Script para Brookhaven RP no Executor Delta local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Criando a Janela Principal local Window = Library.CreateLib("Kaka Hub v2", "DarkTheme")

-- Criando as Abas local HomeTab = Window:NewTab("Início") local HouseTab = Window:NewTab("Casas") local CommandsTab = Window:NewTab("Comandos") local AvatarTab = Window:NewTab("Avatar")

-- Variáveis globais local selectedHouse = "" local hubVisible = true

-- Seção de Início local HomeSection = HomeTab:NewSection("Bem-vindo ao Kaka Hub") HomeSection:NewLabel("Discord: https://discord.gg/AQSbuqVt") HomeSection:NewButton("Fechar/Abrir Hub", "Mostra ou esconde o Hub", function() hubVisible = not hubVisible Window:ToggleUI(hubVisible) end)

-- Aba de Casas local HouseSection = HouseTab:NewSection("Gerenciamento de Casas") HouseSection:NewTextBox("Número da Casa", "Digite o número da casa", function(houseNumber) selectedHouse = houseNumber print("Casa selecionada: " .. selectedHouse) end)

HouseSection:NewButton("Pegar Permissão", "Pega permissão da casa selecionada", function() if selectedHouse ~= "" then game:GetService("ReplicatedStorage"):FindFirstChild("HousePermissionEvent"):FireServer(selectedHouse) print("Permissão concedida para a casa: " .. selectedHouse) else print("Por favor, insira um número de casa primeiro.") end end)

HouseSection:NewButton("Remover Banimento", "Remove o banimento da casa selecionada", function() if selectedHouse ~= "" then game:GetService("ReplicatedStorage"):FindFirstChild("UnbanHouseEvent"):FireServer(selectedHouse) print("Banimento removido da casa: " .. selectedHouse) else print("Por favor, insira um número de casa primeiro.") end end)

-- Aba de Comandos local CommandsSection = CommandsTab:NewSection("Comandos") CommandsSection:NewButton("Infinite Yield", "Executa Infinite Yield", function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end)

CommandsSection:NewButton("Fly v3", "Ativa o Fly v3", function() loadstring(game:HttpGet("https://pastebin.com/raw/CaCqj3nX"))() end)

CommandsSection:NewButton("TP Tool", "Ativa a TP Tool", function() loadstring(game:HttpGet("https://pastebin.com/raw/jb74fX1K"))() end)

-- Aba de Avatar local AvatarSection = AvatarTab:NewSection("Avatar") AvatarSection:NewButton("Abrir Catálogo", "Abre o catálogo de avatares do Roblox", function() game:GetService("CoreGui"):SetCoreGuiEnabled(Enum.CoreGuiType.Catalog, true) print("Catálogo de avatares aberto!") end)

print("Kaka Hub carregado com sucesso!")

