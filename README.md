-- Carrega a biblioteca de interface do usuário local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()

-- Cria a janela principal local Window = Library.CreateLib("Kaka Hub v1", "DarkTheme")

-- Mensagem de boas-vindas local WelcomeScreen = Instance.new("ScreenGui", game.CoreGui) local WelcomeText = Instance.new("TextLabel", WelcomeScreen) WelcomeText.Size = UDim2.new(0, 400, 0, 50) WelcomeText.Position = UDim2.new(0.5, -200, 0.2, 0) WelcomeText.Text = "Bem-vindo ao Kaka Hub!" WelcomeText.TextSize = 24 WelcomeText.BackgroundTransparency = 1 WelcomeText.TextColor3 = Color3.new(1, 1, 1) wait(3) WelcomeScreen:Destroy()

-- Aba Principal local MainTab = Window:NewTab("Principal") local MainSection = MainTab:NewSection("Bem-vindo ao Kaka Hub!")

-- Aba de Casas local HousesTab = Window:NewTab("Casas") local HousesSection = HousesTab:NewSection("Gerenciamento de Casas")

-- Campo de entrada para o número da casa local HouseNumber = "1" HousesSection:NewTextBox("Número da Casa", "Digite o número da casa", function(value) HouseNumber = tonumber(value) or 1 end)

-- Botão para remover banimento de casas HousesSection:NewButton("Desbanir de Casa", "Remove o banimento da casa especificada.", function() if game.ReplicatedStorage:FindFirstChild("BannedLots") then game.ReplicatedStorage.BannedLots:Destroy() end end)

-- Botão para obter permissão de casa HousesSection:NewButton("Obter Permissão de Casa", "Obtém permissão para a casa especificada.", function() if HouseNumber then local args = { [1] = "Roommate", [2] = HouseNumber } game:GetService("ReplicatedStorage").Events.Request:FireServer(unpack(args)) end end)

-- Aba de Gamepasses Grátis local GamepassTab = Window:NewTab("Gamepasses") local GamepassSection = GamepassTab:NewSection("Gamepasses Grátis")

GamepassSection:NewButton("Obter Todas Gamepasses", "Ativa todas as gamepasses do Brookhaven.", function() local Passes = {"Premium", "Music", "VehiclePack", "Estate", "SWAT", "Speed", "Unicorn", "Firefighter", "SpecialForces"} for _, pass in pairs(Passes) do game:GetService("Players").LocalPlayer[pass] = true end end)

-- Aba para abrir o Catálogo do Roblox local CatalogTab = Window:NewTab("Catálogo") local CatalogSection = CatalogTab:NewSection("Editar Avatar")

CatalogSection:NewButton("Abrir Catálogo", "Abre o catálogo do Roblox para edição do avatar.", function() game:GetService("GuiService"):OpenBrowserWindow("https://www.roblox.com/catalog") end)

-- Aba de Comandos local CommandsTab = Window:NewTab("Comandos") local CommandsSection = CommandsTab:NewSection("Comandos Administrativos")

-- Botão para carregar o Infinite Yield CommandsSection:NewButton("Carregar Infinite Yield", "Carrega o Infinite Yield para comandos adicionais.", function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end)

-- Aba de Áudio local AudioTab = Window:NewTab("Áudio") local AudioSection = AudioTab:NewSection("Tocar Música")

-- Campo de entrada para ID da música local MusicID = "" AudioSection:NewTextBox("ID da Música", "Digite o ID da música do Roblox", function(value) MusicID = tonumber(value) or "" end)

-- Botão para tocar música AudioSection:NewButton("Tocar Música", "Reproduz a música com o ID inserido.", function() if MusicID ~= "" then local sound = Instance.new("Sound", game.Workspace) sound.SoundId = "rbxassetid://" .. MusicID sound:Play() end end)

