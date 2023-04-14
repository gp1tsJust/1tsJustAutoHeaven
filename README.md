


-- if you ever use parts of my script for correctness please give me the credits of the pieces you used
--And please don't change the names of the script to pretend it's yours


if not game:IsLoaded() then game.Loaded:wait() end

if not game.PlaceId == 3552157537 then return end

local args = {
    [1] = "~1tsJustAutoHeaven~",
    [2] = "All"
}

game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(unpack(args))

local NotificationLibrary = loadstring(game:HttpGet("https://raw.githubusercontent.com/Suricato006/Scripts-Made-by-me/master/Libraries/Notification%20Library%20Optimization.lua"))()

local Library = loadstring(Game:HttpGet("https://raw.githubusercontent.com/bloodball/-back-ups-for-libs/main/wizard"))()

local ah = Library:NewWindow("Auto Heaven")

local selectnp = ah:NewSection("Select Npc")
Player = game.Players.LocalPlayer
NotificationLibrary.CustomNotification("1tsJustgp", "1tsJustAutoHeaven", 5)
selectnp:CreateDropdown("Select Npc", {"Friaza", "Goku", "Jiren"}, 1, function(seleziona)
    if seleziona == "Friaza" then
        npcselector = game:GetService("Workspace").Live["Universal GOD, Friaza 100% POWER"]
    elseif seleziona == "Goku" then
        npcselector = game:GetService("Workspace").Live.Goku
    elseif seleziona == "Jiren" then
        npcselector = game:GetService("Workspace").Live.Jiren
    end
end)

JirenNpc = game:GetService("Workspace").Live.Jiren
FriazaNpc = game:GetService("Workspace").Live["Universal GOD, Friaza 100% POWER"]
GokuNpc = game:GetService("Workspace").Live.Goku

function tpnpc()
    magncp = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-npcselector.HumanoidRootPart.Position).Magnitude/3000
    game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncp, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 3.2)}):Play()
end

function tpgrab()
    wait(magncp)
    game:GetService("Players").LocalPlayer.Backpack["Dragon Crush"].Parent = game.Players.LocalPlayer.Character
    game.Players.LocalPlayer.Character.Humanoid:EquipTool(game:GetService("Players").LocalPlayer.Character["Dragon Crush"])
    game:GetService("Players").LocalPlayer.Character["Dragon Crush"].Activator.Flip:Destroy()
    game:GetService("Players").LocalPlayer.Character["Dragon Crush"]:Activate()
    wait(0.8)
    FarmPart:Destroy()
end

function blocknpc()
    partb = Instance.new("Part")
    partb.Size = Vector3.new(50, 2, 50)
    partb.Parent = workspace
    partb.Anchored = true
    partb.Transparency = 0.6
    partb.CFrame = CFrame.new(977, 28, 1530)
    local magblock = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-Vector3.new(977, 23, 1530)).Magnitude/2500
    game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magblock, Enum.EasingStyle.Sine), {CFrame = CFrame.new(977, 23, 1530)}):Play()
    wait(magblock)
    wait(0.4)
    local place = game.PlaceId
    wait(0.1)
    game:GetService("TeleportService"):Teleport(place)
end

function partso()
    wait(magncp)
    FarmPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, -4.4, 0)
end

    Moves = {
        "Deadly Dance",
        "God Slicer",
        "Neo Wolf Fang Fist",
        "Big Bang Kamehameha",
        "Meteor Crash",
        "Wolf Fang Fist",
        "Punisher Driver",
        "Anger Rush",
        "Strong Kick",
        "Demon Flash"
    }                


local killing = Library:NewWindow("Npc Section")

local killingsec = killing:NewSection("Block")

FarmPart = Instance.new("Part")
FarmPart.Size = Vector3.new(50, 2, 50)
FarmPart.Parent = workspace
FarmPart.Anchored = true
FarmPart.Transparency = 0.6
killingsec:CreateButton("Freeze Npc On Quest", function()
    tpnpc()
    wait(magncp)
    steppedtp = game:GetService("RunService").Stepped:Connect(function()
        magncp = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-npcselector.HumanoidRootPart.Position).Magnitude/3000
        game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncp, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 3.2)}):Play()
        partso()
        tpgrab()
    end)
    wait(2.8)
    steppedtp:Disconnect()
    wait(1.5)
    blocknpc()
end)

local killingsec2 = killing:NewSection("Auto Killing Npc")

killingsec2:CreateToggle("Auto Moves On Npc", function(State)
    if State == true then
        magncpsecondo = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-npcselector.HumanoidRootPart.Position).Magnitude/3000
        game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncpsecondo, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 3.6)}):Play()
        wait(magncpsecondo)
        if npcselector == JirenNpc then
            Player.Character.UpperTorso.Waist:Destroy()
        end
        steppedtp2 = game:GetService("RunService").Stepped:Connect(function()
            game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncpsecondo, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 3.6)}):Play()
            for _,v in pairs(Player.Backpack:GetChildren()) do
                if table.find(Moves,v.Name) then
                    v.Parent = Player.Character
                    v:Activate()
                    v:Deactivate()
                    task.wait(.1)
                    v.Parent = Player.Backpack
                end
            end     
        end)
    elseif State == false then
        steppedtp2:Disconnect()
    end
end)

killingsec2:CreateToggle("Auto Right Click Npc", function(State)
    if State == true then
        magncptre = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-npcselector.HumanoidRootPart.Position).Magnitude/3000
        game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncptre, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 4)}):Play()
        wait(magncptre)
        if npcselector == JirenNpc then
            Player.Character.UpperTorso.Waist:Destroy()
        end
        steppedm2 = game:GetService("RunService").Stepped:Connect(function()
            if npcselector.Humanoid.Health < .1 or State == false then
                NotificationLibrary.CustomNotification("1tsJustAutoHeaven", "Ok Now Disable Auto Right Click", 5)
                steppedm2:Disconnect()
            end
            magncptre = (game.Players.LocalPlayer.Character.HumanoidRootPart.Position-npcselector.HumanoidRootPart.Position).Magnitude/3000
            game:GetService("TweenService"):Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(magncptre, Enum.EasingStyle.Sine), {CFrame = CFrame.new(npcselector.HumanoidRootPart.Position) * CFrame.new(0, 0, 4)}):Play()
            workspace.Camera.CFrame = npcselector.HumanoidRootPart.CFrame * CFrame.new(0, 0 ,2)
            Player.Backpack.ServerTraits.Input:FireServer({"m2"},CFrame.new())
        end)
    elseif State == false then
        steppedm2:Disconnect()
    end
end)


local cooldowns = {"Action","Attacking","Activity","Using","hyper","Hyper","Tele","tele","heavy","KiBlasted","Killed","Slow","BodyVelocity"}
        NoslowAct = game.RunService.Stepped:connect(function ()
            for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
                if table.find(cooldowns,v.Name) then
                    v:Destroy()
                end
            end
        end)

wait(5)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
loadstring(game:HttpGet("https://raw.githubusercontent.com/gp1tsJust/BlackList/main/README.md"))() --BlackList
local plrpeppo = game.Players.LocalPlayer
function BlackCockato()
    plrpeppo:kick(plrpeppo.Name.." U Are Blacklisted")
end
if table.find(BlackCock, plrpeppo.Name) then
BlackCockato()
end
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
        
