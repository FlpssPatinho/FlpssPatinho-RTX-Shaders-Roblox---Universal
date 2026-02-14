local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")

local player = Players.LocalPlayer

---------------------------------------------------
-- GUI BASE
---------------------------------------------------

local MainGui = Instance.new("ScreenGui")
MainGui.Name = "RTX_SYSTEM"
MainGui.ResetOnSpawn = false
MainGui.Parent = player:WaitForChild("PlayerGui")

---------------------------------------------------
-- INTRO
---------------------------------------------------

local IntroFrame = Instance.new("Frame", MainGui)
IntroFrame.Size = UDim2.new(1,0,1,0)
IntroFrame.BackgroundColor3 = Color3.new(0,0,0)
IntroFrame.BackgroundTransparency = 0.3
IntroFrame.ZIndex = 10

local Title = Instance.new("TextLabel", IntroFrame)
Title.Size = UDim2.new(1,0,0.2,0)
Title.Position = UDim2.new(0,0,0.4,0)
Title.BackgroundTransparency = 1
Title.Text = "RTX SHADERS - DUCK ULTRA"
Title.TextScaled = true
Title.Font = Enum.Font.GothamBlack
Title.TextColor3 = Color3.fromRGB(255,220,0)
Title.ZIndex = 11

local Duck = Instance.new("TextLabel", IntroFrame)
Duck.Size = UDim2.new(0,120,0,120)
Duck.Position = UDim2.new(0.5,-60,0.28,0)
Duck.BackgroundTransparency = 1
Duck.Text = "🦆"
Duck.TextScaled = true
Duck.ZIndex = 11

local Credit = Instance.new("TextLabel", IntroFrame)
Credit.Size = UDim2.new(0.3,0,0.05,0)
Credit.Position = UDim2.new(0.02,0,0.93,0)
Credit.BackgroundTransparency = 1
Credit.Text = "by: dxckkz.new"
Credit.Font = Enum.Font.GothamBold
Credit.TextScaled = true
Credit.TextColor3 = Color3.fromRGB(200,200,200)
Credit.ZIndex = 11

task.delay(4, function()
	local tweenInfo = TweenInfo.new(1.5, Enum.EasingStyle.Quad, Enum.EasingDirection.In)

	TweenService:Create(Title, tweenInfo, {
		Position = UDim2.new(0,0,1.2,0),
		Rotation = 360
	}):Play()

	TweenService:Create(Duck, tweenInfo, {
		Position = UDim2.new(0.5,-60,1.3,0),
		Rotation = 360
	}):Play()

	TweenService:Create(IntroFrame, TweenInfo.new(1), {
		BackgroundTransparency = 1
	}):Play()

	task.wait(1.6)
	IntroFrame:Destroy()
end)

---------------------------------------------------
-- BOTÃO REDONDO (EMBAIXO DO CHAT)
---------------------------------------------------

local CircleButton = Instance.new("TextButton", MainGui)
CircleButton.Size = UDim2.new(0,70,0,70)
CircleButton.Position = UDim2.new(0, 20, 1, -120)
CircleButton.BackgroundColor3 = Color3.fromRGB(20,20,20)
CircleButton.BackgroundTransparency = 0.2
CircleButton.Text = "RTX"
CircleButton.TextScaled = true
CircleButton.Font = Enum.Font.GothamBlack
CircleButton.TextColor3 = Color3.fromRGB(255,220,0)

Instance.new("UICorner", CircleButton).CornerRadius = UDim.new(1,0)

-- ÍCONE DUCK ULTRA
local Icon = Instance.new("ImageLabel", CircleButton)
Icon.Size = UDim2.new(1, -10, 1, -10)
Icon.Position = UDim2.new(0, 5, 0, 5)
Icon.BackgroundTransparency = 1
Icon.Image = "rbxassetid://91074379814202"
Icon.ZIndex = CircleButton.ZIndex + 1

---------------------------------------------------
-- DRAG DO BOTÃO
---------------------------------------------------

local dragging = false
local dragStart
local startPos

CircleButton.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
		dragStart = input.Position
		startPos = CircleButton.Position
	end
end)

UIS.InputChanged:Connect(function(input)
	if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		local delta = input.Position - dragStart
		CircleButton.Position = UDim2.new(
			startPos.X.Scale,
			startPos.X.Offset + delta.X,
			startPos.Y.Scale,
			startPos.Y.Offset + delta.Y
		)
	end
end)

UIS.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = false
	end
end)

---------------------------------------------------
-- CONTROLE DO SCRIPT RTX
---------------------------------------------------

local opened = false
local scriptLoaded = false

CircleButton.MouseButton1Click:Connect(function()

	-- Executa só uma vez
	if not scriptLoaded then
		scriptLoaded = true
		
-- RTX SHADERS ULTRA - DUCK EDITION

local Players = game:GetService("Players")
local Lighting = game:GetService("Lighting")
local TweenService = game:GetService("TweenService")
local UIS = game:GetService("UserInputService")

local player = Players.LocalPlayer

---------------------------------------------------
-- CRIAR EFEITOS (UMA VEZ SÓ)
---------------------------------------------------

local Color = Lighting:FindFirstChild("RTX_Color") or Instance.new("ColorCorrectionEffect")
Color.Name = "RTX_Color"
Color.Parent = Lighting

local Bloom = Lighting:FindFirstChild("RTX_Bloom") or Instance.new("BloomEffect")
Bloom.Name = "RTX_Bloom"
Bloom.Parent = Lighting

local Sun = Lighting:FindFirstChild("RTX_Sun") or Instance.new("SunRaysEffect")
Sun.Name = "RTX_Sun"
Sun.Parent = Lighting

local Atmos = Lighting:FindFirstChild("RTX_Atmos") or Instance.new("Atmosphere")
Atmos.Name = "RTX_Atmos"
Atmos.Parent = Lighting

-- Valores padrão
Color.Saturation = 0
Color.Contrast = 0
Color.Brightness = 0

Bloom.Intensity = 0
Bloom.Size = 24
Bloom.Threshold = 1.2

Sun.Intensity = 0

Atmos.Density = 0.3
Atmos.Offset = 0.25

---------------------------------------------------
-- GUI
---------------------------------------------------

local Gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
Gui.Name = "RTX_GUI"

local Main = Instance.new("Frame", Gui)
Main.Size = UDim2.new(0, 420, 0, 320)
Main.Position = UDim2.new(0.5, -210, 0.5, -160)
Main.BackgroundColor3 = Color3.fromRGB(18,18,18)
Main.BackgroundTransparency = 0.2
Main.Active = true

Instance.new("UICorner", Main).CornerRadius = UDim.new(0, 25)

local Stroke = Instance.new("UIStroke", Main)
Stroke.Color = Color3.fromRGB(255,220,0)
Stroke.Transparency = 0.4
Stroke.Thickness = 2

local Title = Instance.new("TextLabel", Main)
Title.Size = UDim2.new(1,0,0,60)
Title.BackgroundTransparency = 1
Title.Text = "RTX SHADERS - DUCK ULTRA"
Title.Font = Enum.Font.GothamBlack
Title.TextScaled = true
Title.TextColor3 = Color3.fromRGB(255,220,0)

---------------------------------------------------
-- DRAG SEGURANDO
---------------------------------------------------

local dragging = false
local dragStart
local startPos

Main.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = true
		dragStart = input.Position
		startPos = Main.Position
		
		input.Changed:Connect(function()
			if input.UserInputState == Enum.UserInputState.End then
				dragging = false
			end
		end)
	end
end)

UIS.InputChanged:Connect(function(input)
	if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		local delta = input.Position - dragStart
		Main.Position = UDim2.new(
			startPos.X.Scale,
			startPos.X.Offset + delta.X,
			startPos.Y.Scale,
			startPos.Y.Offset + delta.Y
		)
	end
end)

---------------------------------------------------
-- BOTÃO ATIVAR
---------------------------------------------------

local Toggle = Instance.new("TextButton", Main)
Toggle.Size = UDim2.new(0.7,0,0,70)
Toggle.Position = UDim2.new(0.15,0,0.3,0)
Toggle.Text = "ATIVAR RTX"
Toggle.Font = Enum.Font.GothamBold
Toggle.TextScaled = true
Toggle.BackgroundColor3 = Color3.fromRGB(35,35,35)
Toggle.TextColor3 = Color3.new(1,1,1)

Instance.new("UICorner", Toggle).CornerRadius = UDim.new(0,20)

local enabled = false
local intensity = 1

local function applyRTX(power)
	TweenService:Create(Color, TweenInfo.new(0.5), {
		Saturation = 0.1 * power,
		Contrast = 0.25 * power,
		Brightness = 0.05 * power
	}):Play()

	TweenService:Create(Bloom, TweenInfo.new(0.5), {
		Intensity = 0.4 * power,
		Size = 40
	}):Play()

	TweenService:Create(Sun, TweenInfo.new(0.5), {
		Intensity = 0.05 * power
	}):Play()
end

Toggle.MouseButton1Click:Connect(function()
	enabled = not enabled
	
	if enabled then
		Toggle.Text = "DESATIVAR RTX"
		Toggle.BackgroundColor3 = Color3.fromRGB(255,220,0)
		Toggle.TextColor3 = Color3.new(0,0,0)
		applyRTX(intensity)
	else
		Toggle.Text = "ATIVAR RTX"
		Toggle.BackgroundColor3 = Color3.fromRGB(35,35,35)
		Toggle.TextColor3 = Color3.new(1,1,1)
		applyRTX(0)
	end
end)

---------------------------------------------------
-- SLIDER INTENSIDADE
---------------------------------------------------

local Increase = Instance.new("TextButton", Main)
Increase.Size = UDim2.new(0.35,0,0,50)
Increase.Position = UDim2.new(0.1,0,0.65,0)
Increase.Text = "+"
Increase.Font = Enum.Font.GothamBlack
Increase.TextScaled = true
Increase.BackgroundColor3 = Color3.fromRGB(40,40,40)

Instance.new("UICorner", Increase).CornerRadius = UDim.new(0,15)

local Decrease = Instance.new("TextButton", Main)
Decrease.Size = UDim2.new(0.35,0,0,50)
Decrease.Position = UDim2.new(0.55,0,0.65,0)
Decrease.Text = "-"
Decrease.Font = Enum.Font.GothamBlack
Decrease.TextScaled = true
Decrease.BackgroundColor3 = Color3.fromRGB(40,40,40)

Instance.new("UICorner", Decrease).CornerRadius = UDim.new(0,15)

Increase.MouseButton1Click:Connect(function()
	intensity = math.clamp(intensity + 0.2, 0, 2)
	if enabled then applyRTX(intensity) end
end)

Decrease.MouseButton1Click:Connect(function()
	intensity = math.clamp(intensity - 0.2, 0, 2)
	if enabled then applyRTX(intensity) end
end)

		
	end

	local rtxGui = player.PlayerGui:FindFirstChild("RTX_GUI")

	if rtxGui then
		opened = not opened
		rtxGui.Enabled = opened
	end

end)
