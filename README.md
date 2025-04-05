--// Kaka Hub - Brookhaven RP Script // local KakaHub = Instance.new("ScreenGui") local MainFrame = Instance.new("Frame") local HubButton = Instance.new("TextButton") local HomeTab = Instance.new("Frame") local HousesTab = Instance.new("Frame") local CommandsTab = Instance.new("Frame") local AvatarTab = Instance.new("Frame")

--// Properties // KakaHub.Name = "KakaHub" KakaHub.Parent = game.CoreGui

MainFrame.Name = "MainFrame" MainFrame.Parent = KakaHub MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30) MainFrame.Size = UDim2.new(0, 300, 0, 400) MainFrame.Position = UDim2.new(0.5, -150, 0.5, -200) MainFrame.Draggable = true MainFrame.Active = true

HubButton.Name = "HubButton" HubButton.Parent = KakaHub HubButton.Size = UDim2.new(0, 50, 0, 50) HubButton.Position = UDim2.new(0, 10, 0, 10) HubButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0) HubButton.Text = "HUB" HubButton.MouseButton1Click:Connect(function() MainFrame.Visible = not MainFrame.Visible end)

--// Home Tab - Discord Link // local DiscordLabel = Instance.new("TextLabel", HomeTab) DiscordLabel.Size = UDim2.new(1, 0, 0, 50) DiscordLabel.Text = "Discord: https://discord.gg/AQSbuqVt" DiscordLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

--// Houses Tab // local HouseNumberBox = Instance.new("TextBox", HousesTab) HouseNumberBox.PlaceholderText = "Número da casa"

local GetPermissionButton = Instance.new("TextButton", HousesTab) GetPermissionButton.Text = "Pegar Permissão" GetPermissionButton.MouseButton1Click:Connect(function() local houseNumber = tonumber(HouseNumberBox.Text) if houseNumber then game:GetService("ReplicatedStorage").Events.GiveHousePermissions:FireServer(houseNumber) end end)

local UnbanButton = Instance.new("TextButton", HousesTab) UnbanButton.Text = "Remover Ban" UnbanButton.MouseButton1Click:Connect(function() local houseNumber = tonumber(HouseNumberBox.Text) if houseNumber then game:GetService("ReplicatedStorage").Events.UnbanPlayer:FireServer(houseNumber) end end)

--// Commands Tab // local InfiniteYieldButton = Instance.new("TextButton", CommandsTab) InfiniteYieldButton.Text = "Abrir Infinite Yield" InfiniteYieldButton.MouseButton1Click:Connect(function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end)

local FlyButton = Instance.new("TextButton", CommandsTab) FlyButton.Text = "Fly v3" FlyButton.MouseButton1Click:Connect(function() loadstring(game:HttpGet("https://pastebin.com/raw/6GU5d3ak"))() end)

local TpToolButton = Instance.new("TextButton", CommandsTab) TpToolButton.Text = "TP Tool" TpToolButton.MouseButton1Click:Connect(function() local tool = Instance.new("Tool") tool.RequiresHandle = false tool.Name = "TP Tool" tool.Activated:Connect(function() local pos = game:GetService("Players").LocalPlayer:GetMouse().Hit.p game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(pos) end) tool.Parent = game:GetService("Players").LocalPlayer.Backpack end)

--// Avatar Tab // local OpenCatalogButton = Instance.new("TextButton", AvatarTab) OpenCatalogButton.Text = "Abrir Catálogo" OpenCatalogButton.MouseButton1Click:Connect(function() game:GetService("GuiService"):OpenCatalog() end)

return KakaHub

