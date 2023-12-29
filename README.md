-- No Doors Hub 1.0

local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

local Window = OrionLib:MakeWindow({Name = "No gui", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})
                                                  

local MainTab = Window:MakeTab({
	Name = "Main guis",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = MainTab:AddSection({
	Name = "EnjoyðŸ‘Œ"
})

MainTab:AddSlider({
	Name = "WalkSpeed Slider",
	Min = 16,
	Max = 50,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "WS",
	Callback = function(Value)
		game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
	end    
})

MainTab:AddButton({
	Name = "MSDOORS ",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/mstudio45/MSDOORS/7bd97c2d956a775d683c2d7973d79715b30998ea/MSDOORS/Moonsec.lua'))()
  	end    
})

MainTab:AddButton({
	Name = "MSDOORShub",
	Callback = function()
        loadstring(game:HttpGet(("https://raw.githubusercontent.com/mstudio45/MSDOORS/main/MSHUB_Loader.lua"),true))()           
  	end    
})

MainTab:AddButton({
	Name = "King Hub",
	Callback = function()
        loadstring(game:HttpGetAsync("https://pastebin.com/raw/R8QMbhzv"))()
  	end    
})

MainTab:AddButton({
	Name = "awesome pc",
	Callback = function()
        loadstring(game:HttpGet("https://lolcat.boo/awesomescript"))()
  	end    
})

MainTab:AddButton({
	Name = "Vynixius",
	Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/RegularVynixu/Vynixius/main/Doors/Script.lua"))()
  	end    
})

MainTab:AddButton({
	Name = "awesome mobile",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/yieviro92creepy/Ak/main/Z'))()
  	end    
})

MainTab:AddButton({
	Name = "poopdoors",
	Callback = function()
        loadstring(game:HttpGet('https://raw.githubusercontent.com/zoophiliaphobic/POOPDOORS/main/script.lua'))()
  	end    
})
MainTab:AddButton({
	Name = "no hub ",
	Callback = function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/ha2ke3oer/No-hub/main/README.md"))()
  	end    
})
local OtherTab = Window:MakeTab({
	Name = "Other scripts",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = OtherTab:AddSection({
	Name = "Other cool scripts"
})

OtherTab:AddButton({
	Name = "Fe Tornado Script",
	Callback = function()
		_G.spinSpeed = 500

		local plr = game.Players.LocalPlayer
		local char = plr.Character or plr.CharacterAppearanceLoaded:Wait()
		local hrp = char:FindFirstChild("HumanoidRootPart") or char:FindFirstChild("Collision") or char:FindFirstChildOfClass("BasePart")
		local spinningAttachments = {}
		local mainAttachment = Instance.new("Attachment",hrp)
		mainAttachment.Name = "MainAttachment"
		for i=1, 10 do
			local spinningAttachment = Instance.new("Attachment",mainAttachment)
			spinningAttachments[#spinningAttachments+1] = spinningAttachment
			spinningAttachment.Position = Vector3.new(0,-2,0)
			spinningAttachment:SetAttribute("i",i)
		end
		for _,spinningAttachment in pairs(spinningAttachments) do
			local i = spinningAttachment:GetAttribute("i")
			coroutine.wrap(function()
				local rot = 0
				while true do
					spinningAttachment.Orientation = Vector3.new(0,rot,0)
					rot += (tonumber(_G.spinSpeed) ~= nil and tonumber(_G.spinSpeed) or 1)*(5/i)
					if rot == 360 or rot >= 360 then
						rot = 0
					end
					task.wait(0)
				end
				spinningAttachment:Destroy()
			end)()
		end
		function isnumber(a)
			a = tostring(a)
			return tonumber(a) ~= nil or a == "inf" or a == "-inf" or a == "nan"
		end
		function rs(times)
			local times = times or 1
			if times == 0 or times <= 0 then
				times = 1
			end
			times = (times-1)*game["Run Service"].RenderStepped:Wait()
			if math.floor(times) == 0 then
				times = 1
			end
			for i=1,times do
				game["Run Service"].RenderStepped:Wait()
			end
		end
		function tornadoo(d)
			if not d or not d:IsA("BasePart") then return end
			d.Massless = true
			d.CanTouch = false
			coroutine.wrap(function()
				if d and d:IsDescendantOf(workspace) then
					local spinAttachment = Instance.new("Attachment",spinningAttachments[math.random(1,#spinningAttachments)])
					spinAttachment.Position = Vector3.new(math.random(1,2) == 1 and 5 or -5,math.random(0,100)/10,math.random(1,2) == 1 and 5 or -5)
					spinAttachment.Position -= Vector3.new(0,0,spinAttachment.Position.Y*2)
					local holderAttachment = Instance.new("Attachment",d)
					holderAttachment.Orientation = Vector3.new(math.random(-179,179),math.random(-179,179),math.random(-179,179))
					local aP = Instance.new("AlignPosition",d)
					aP.Attachment1 = spinAttachment
					aP.Attachment0 = holderAttachment
					aP.MaxForce = 50
					aP.Responsiveness = 50
					aP.ApplyAtCenterOfMass = true
					local aO = Instance.new("AlignOrientation",d)
					aO.Attachment1 = aP.Attachment1
					aO.Attachment0 = aP.Attachment0
					local rotVector = Vector3.new(math.random(-10,10),math.random(-10,10),math.random(-10,10))
					coroutine.wrap(function()
						repeat
							rotVector += Vector3.new(math.random(-100,100)/5000,math.random(-100,100)/5000,math.random(-100,100)/5000)
							holderAttachment.Orientation -= rotVector
							rs(1)
						until not d or not d:IsDescendantOf(workspace)
						rs(1)
						spinAttachment:Destroy()
						if d then
							aP:Destroy()
							aO:Destroy()
						end
					end)()
				end
			end)()
		end
		function descendant(d)
			coroutine.wrap(function()
				if d then
					if d:IsA("BasePart") then
						rs(5)
						if d.Name == "Door" and d.Parent.Name == "DoorSet" then
							rs(1)
							tornadoo(d)
						end
						if d.Name == "Door" and d.Parent.Name == "DoorNormal" then
							rs(1)
							tornadoo(d)
						end
						if d.Name == "BananaPeel" then
							rs(1)
							tornadoo(d)
						end
					end
					if d:IsA("Folder") then
						rs(5)
						if d.Name == "FigureSetup" then
							for i,v in pairs(d:GetDescendants()) do
								tornadoo(d)
							end
						end
					end
					if d:IsA("Model") and not d:IsA("Tool") then
						if d.Name == "JeffTheKiller" or d.Name == "Jeff the killer" then
							rs(1)
							for i,v in pairs(d:GetDescendants()) do
								tornadoo(d)
							end
						end
						if d.Name == "DrawerContainer" then
							rs(1)
							tornadoo(d:WaitForChild("Main"))
						end
						if d.Name == "Door" and isnumber(d.Parent.Name) then
							rs(1)
							tornadoo(d:WaitForChild("Door"))
						end
					end
					if d:IsA("PrismaticConstraint") or d:IsA("HingeConstraint") then
						rs(1)
						d:Destroy()
					end
				end
			end)()
		end
		for i,v in pairs(workspace:GetDescendants()) do
			descendant(v)
		end
		workspace.DescendantAdded:Connect(descendant)
		print("Success!")
		game["Run Service"].RenderStepped:Connect(function()
			mainAttachment.WorldOrientation = Vector3.new()
		end)
  	end    
})


OtherTab:AddButton({
	Name = "Remove Door 50 NOT FE",
	Callback = function()
		game:GetService("Workspace").CurrentRooms:FindFirstChild("50").Door.Door:remove()
  	end    
})

OtherTab:AddButton({
	Name = "Shears on everything",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/MrNeRD0/Doors-Hack/main/shears_done.lua"))()
  	end    
})


OtherTab:AddButton({
	Name = "Sally/Window on ever door",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/therealderkleinetiger/Doors-Public/main/Sally%20on%20every%20Window.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "Tablet In Shop",
	Callback = function()
		_G.UpdateStars = false -- stars disappear after picking up a book/breaker pole | false: a little lag
_G.OnShop = true -- can buy on pre run shop
_G.Price = 1 -- tablet price on shop
_G.Description = "FREE IPAD" -- tablet description on shop

loadstring(game:HttpGet('https://raw.githubusercontent.com/DeividComSono/Scripts/main/Scanner.lua'))()
  	end    
})

OtherTab:AddButton({
	Name = "Noclip",
	Callback = function()
		local Noclip = nil
local Clip = nil

function noclip()
	Clip = false
	local function Nocl()
		if Clip == false and game.Players.LocalPlayer.Character ~= nil then
			for _,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
				if v:IsA('BasePart') and v.CanCollide and v.Name ~= floatName then
					v.CanCollide = false
				end
			end
		end
		wait(0.21) -- basic optimization
	end
	Noclip = game:GetService('RunService').Stepped:Connect(Nocl)
end

function clip()
	if Noclip then Noclip:Disconnect() end
	Clip = true
end

noclip() -- to toggle noclip() and clip()
  	end    
})

OtherTab:AddButton({
	Name = "Auto Change Badges",
	Callback = function()
		local list = require(game:GetService("ReplicatedStorage").Achievements)
while task.wait() do
    for i,v in pairs(list) do 
        game:GetService("ReplicatedStorage").EntityInfo.FlexAchievement:FireServer(i)
    end
end
  	end    
})

OtherTab:AddButton({
	Name = "Noclip + Bypasser",
	Callback = function()
		-- Made by Deivid#5444

_G.Keybind = "R"
_G.ClipGui = true
_G.IncludeNoclip = true

local isEnabled = false

local UIS = game:GetService("UserInputService")

local Plr = game.Players.LocalPlayer
local Char = Plr.Character or Plr.CharacterAdded:Wait()

local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Parent = game.CoreGui
ScreenGui.Enabled = _G.ClipGui or false

local TextLabel = Instance.new("TextLabel")
TextLabel.Parent = ScreenGui

TextLabel.AnchorPoint = Vector2.new(1, 0)
TextLabel.Position = UDim2.new(1, -5, 0, 0)
TextLabel.Text = "Noclip + Bypasser: Off"
TextLabel.Size = UDim2.new(0,200,0,75)
TextLabel.TextScaled = true
TextLabel.TextStrokeColor3 = Color3.new(1,1,1)
TextLabel.TextStrokeTransparency = 0
TextLabel.BackgroundTransparency = 1

function getValue()
    local value
    if isEnabled then
        value = "On"
    else
        value = "Off"
    end
    return value
end

UIS.InputBegan:Connect(function(input, gp)
    if gp then return end

    if input.KeyCode == Enum.KeyCode[_G.Keybind] then
        isEnabled = not isEnabled
        task.wait()
        TextLabel.Text = "Noclip + Bypasser: " .. getValue()
    end
end)

game:GetService("RunService").RenderStepped:Connect(function()
    if not Char:FindFirstChild("HumanoidRootPart") then return end
    if _G.IncludeNoclip then
        Char.HumanoidRootPart.CanCollide = not isEnabled
        Char.Collision.CanCollide = not isEnabled
    end

    local HrpCFrame = Char.HumanoidRootPart.CFrame

    local ray = Ray.new(HrpCFrame.Position, HrpCFrame.LookVector * 0.5)
    local part = workspace:FindPartOnRay(ray)
    if part and part.CanCollide == true and isEnabled then
        Char.HumanoidRootPart.Anchored = true
        Char:PivotTo(Char.HumanoidRootPart.CFrame * CFrame.new(0, 1000, 0))
        task.wait()
        Char:PivotTo(Char.HumanoidRootPart.CFrame * CFrame.new(0, 0, -4))
        task.wait()
        Char:PivotTo(Char.HumanoidRootPart.CFrame * CFrame.new(0, -1000, 0))
        task.wait(0.1)
        Char.HumanoidRootPart.Anchored = false
    end
end)
  	end    
})


OtherTab:AddButton({
	Name = "Mincraft debug scripts",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/K0t1n/Public/main/Debug%20Stick"))()
  	end    
})


OtherTab:AddButton({
	Name = "MCDonalds on Door 0 Script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/K0t1n/Public/main/MCDonalds"))()
  	end    
})

OtherTab:AddButton({
	Name = "Gummy Flashlight On Door 0 Script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/K0t1n/Public/main/Gummy%20Flashlight.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "Normal Flashlight Script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/K0t1n/Public/main/Flashlight.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "Laser Gun Script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/K0t1n/Public/main/Laser%20Gun.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "Reset Yourself",
	Callback = function()
		game.Players.LocalPlayer.Character.Humanoid.Health = 0
  	end    
})

OtherTab:AddButton({
	Name = "No Screech",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/rX4Fkmry"))()
  	end    
})

OtherTab:AddButton({
	Name = "Figure Pov Door 100 script",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/hViaKdbk"))()
  	end    
})

OtherTab:AddButton({
	Name = "Figure Pov Door 50 script",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/yAmUcY13"))()
  	end    
})

OtherTab:AddButton({
	Name = "Seek Pov script",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/QPsfr9P4"))()
  	end    
})

OtherTab:AddButton({
	Name = "Old Seek Modle",
	Callback = function()
		loadstring(game:HttpGet("https://pastebin.com/raw/uXY1EAxZ"))()
  	end    
})

OtherTab:AddButton({
	Name = "Holy Hand Grenade On Everything",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/MrNeRD0/Doors-Hack/main/HolyGrenadeByNerd.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "Magnet Script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/MrNeRD0/Doors-Hack/main/MagnetByNerd.lua"))()
  	end    
})

OtherTab:AddButton({
	Name = "CRUCFIX ON EVERYTHING.if your on mobile use mobile keyboard",
	Callback = function()
		_G.Uses = 99999999999
_G.Range = 999
_G.OnAnything = true
_G.Fail = false
loadstring(game:HttpGet('https://raw.githubusercontent.com/PenguinManiack/Crucifix/main/Crucifix.lua'))() 
  	end    
})

OtherTab:AddButton({
	Name = "Godmode",
	Callback = function()
		local Collison = game.Players.LocalPlayer.Character:FindFirstChild("Collision")
Collison.Position = Collison.Position - Vector3.new(0,10,0)
  	end    
})

local MiscTab = Window:MakeTab({
	Name = "Misc",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

local Section = MiscTab:AddSection({
	Name = "other useful script. Im finding more"
})

MiscTab:AddButton({
	Name = "Esp",
	Callback = function()
      		--[[
Script: ESP Script
Details: Nothing much. Its ESP Chams and the different colors are for different teams.
Creds: idk
]]
-- -----------------------------------
--  ___      _   _   _              --
-- / __| ___| |_| |_(_)_ _  __ _ ___--
-- \__ \/ -_)  _|  _| | ' \/ _` (_-<--
-- |___/\___|\__|\__|_|_||_\__, /__/--
--                         |___/    --
-- -----------------------------------
-- -----------------------------------
ALLYCOLOR = {0,255,255}  	--//Color of the ESP  of people on the same team
ENEMYCOLOR =  {255,0,0} 	--//Color of the ESP  of people on NOT the same team
TRANSPARENCY = 0.5			--//Transparency of the ESP
HEALTHBAR_ACTIVATED = true 	--//Renders the Healthbar
--
--

--							!!!Don't Change Anything Below Here Unless You Know What You're Doing!!!

function createFlex()
-- -----------------------------------------------------------------------------------
--[VARIABLES] //Changing may result in Errors!
players = game:GetService("Players") --//Required for PF
faces = {"Front","Back","Bottom","Left","Right","Top"} --//Every possible Enum face
currentPlayer = nil --//Used for the Team-Check
lplayer = players.LocalPlayer --//The LocalPlayer
-- -----------------------------------------------------------------------------------
players.PlayerAdded:Connect(function(p)
currentPlayer = p
p.CharacterAdded:Connect(function(character) --//For when a new Player joins the game 
createESP(character)			
end)		
end)
-- -----------------------------------------------------------------------------------
function checkPart(obj)  if (obj:IsA("Part") or obj:IsA("MeshPart")) and obj.Name~="HumanoidRootPart" then return true end end --//Check if the Part is suitable 
-- -----------------------------------------------------------------------------------
function actualESP(obj) 

for i=0,5 do
surface = Instance.new("SurfaceGui",obj) --//Creates the SurfaceGui
surface.Face = Enum.NormalId[faces[i+1]] --//Adjusts the Face and chooses from the face table
surface.AlwaysOnTop = true

frame = Instance.new("Frame",surface)	--//Creates the viewable Frame
frame.Size = UDim2.new(1,0,1,0)
frame.BorderSizePixel = 0												
frame.BackgroundTransparency = TRANSPARENCY
if currentPlayer.Team == players.LocalPlayer.Team then --//Checks the Players Team
frame.BackgroundColor3 = Color3.new(ALLYCOLOR[1],ALLYCOLOR[2],ALLYCOLOR[3])	--//If in same Team											
else
frame.BackgroundColor3 = Color3.new(ENEMYCOLOR[1],ENEMYCOLOR[2],ENEMYCOLOR[3])	--//If in another Team
end
							
end
end
-- -----------------------------------------------------------------------------------
function createHealthbar(hrp) 
board =Instance.new("BillboardGui",hrp) --//Creates the BillboardGui with HumanoidRootPart as the Parent
board.Name = "total"
board.Size = UDim2.new(1,0,1,0)
board.StudsOffset = Vector3.new(3,1,0)
board.AlwaysOnTop = true

bar = Instance.new("Frame",board) --//Creates the red background
bar.BackgroundColor3 = Color3.new(255,0,0)
bar.BorderSizePixel = 0
bar.Size = UDim2.new(0.2,0,4,0)
bar.Name = "total2"
				
health = Instance.new("Frame",bar) --//Creates the changing green Frame
health.BackgroundColor3 = Color3.new(0,255,0)
health.BorderSizePixel = 0
health.Size = UDim2.new(1,0,hrp.Parent.Humanoid.Health/100,0)
hrp.Parent.Humanoid.Changed:Connect(function(property) --//Triggers when any Property changed
hrp.total.total2.Frame.Size = UDim2.new(1,0,hrp.Parent.Humanoid.Health/100,0) --//Adjusts the size of the green Frame								
end)
end
-- -----------------------------------------------------------------------------------
function createESP(c) --//Checks and calls the proper function
bugfix = c:WaitForChild("Head") --// *Used so the children of the character arent nil.
for i,v in pairs(c:GetChildren()) do
if checkPart(v) then
actualESP(v)
end
end
if HEALTHBAR_ACTIVATED then --//If the user decided to
createHealthbar(c:WaitForChild("HumanoidRootPart")) --//Calls the function of the creation
end
end
-- -----------------------------------------------------------------------------------
for i,people in pairs(players:GetChildren())do
if people ~= players.LocalPlayer then
currentPlayer = people
								--//Used for Players already in the Game
createESP(people.Character)
people.CharacterAdded:Connect(function(character)
createESP(character)			
end)
end
end
-- -----------------------------------------------------------------------------------
end --//End of the entire function

createFlex() --// Does exactly that :)
  	end    
})

MiscTab:AddButton({
	Name = "Fullbright",
	Callback = function()
		game:GetService ("Lighting").Brightness = 2 game:GetService ("Lighting").ClockTime = 14 game:GetService ("Lighting").FogEnd = 100000 game:GetService ("Lighting").GlobalShadows = false game:GetService ("Lighting").OutdoorAmbient = Color3.fromRGB (128, 128, 128)
  	end    
})

MiscTab:AddButton({
	Name = "Infinte Yeild",
	Callback = function()
		loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
  	end    
})

MiscTab:AddButton({
	Name = "Mobile Keyboard script",
	Callback = function()
		loadstring(game:HttpGet("https://raw.githubusercontent.com/advxzivhsjjdhxhsidifvsh/mobkeyboard/main/main.txt", true))()
  	end    
})
