--  Carregando a Redz Library
local Library = loadstring(game:HttpGet("https://pastebin.com/raw/XqZsnzRQ", true))()
workspace.FallenPartsDestroyHeight = -math.huge

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

--  Criando a Janela Principal
local Window = Library:MakeWindow({
    Title = "Kakah Hub | Brookhaven",
    SubTitle = "By: Kakah",
    LoadText = "Carregando Kakah Hub...",
    Flags = "Kakah_Hub"
})

--  Botão de minimizar
Window:AddMinimizeButton({
    Button = { Image = "rbxassetid://129650788577407", BackgroundTransparency = 1 },
    Corner = { CornerRadius = UDim.new(35, 1) },
})

-- Tabs
local Tab1 = Window:MakeTab({"Credits", "info"})
local Tab2 = Window:MakeTab({"Fun", "fun"})
local Tab3 = Window:MakeTab({"Troll", "skull"})
local Tab4 = Window:MakeTab({"Protector", "shield"})
local Tab5= Window:MakeTab({"Avatar", "shirt"})
local Tab6 = Window:MakeTab({"House", "home"})
local Tab7 = Window:MakeTab({"Car", "car"})
local Tab8 = Window:MakeTab({"RGB", "brush"})
local Tab9 = Window:MakeTab({"Music All", "radio"})
local Tab10 = Window:MakeTab({"Music", "music"})

---------------------------------------------------------------------------------------------------------------------------------
-- === Tab 1: Credits === --
---------------------------------------------------------------------------------------------------------------------------------
Tab1:AddSection({"Créditos do Hub"})

Tab1:AddDiscordInvite({
    Name = "Kakah Hub",
    Description = "Sem Discord ainda....",
    Logo = "rbxassetid://129650788577407",
    Invite = "",
})

InfoTab:AddDiscordInvite({

    Name = "Kakah ",

    Description = "Tik Tok",

    Logo = "rbxassetid://129650788577407",

    Invite = "https://www.tiktok.com/@kaykaka2?_t=ZM-90ubEih1BNc&_r=1",

})

-- Detectar Executor
local function detectExecutor()
    if identifyexecutor then
        return identifyexecutor()
    elseif syn then
        return "Synapse X"
    elseif KRNL_LOADED then
        return "KRNL"
    elseif is_sirhurt_closure then
        return "SirHurt"
    elseif pebc_execute then
        return "ProtoSmasher"
    elseif getexecutorname then
        return getexecutorname()
    else
        return "Executor Desconhecido"
    end
end

local executorName = detectExecutor()
Tab1:AddParagraph({"Executor", executorName})
Tab1:AddSection({"Versão do Hub: 2.1"})
Tab1:AddParagraph({"Developer", "Kakah"})
Tab1:AddParagraph({"Créditos", "ninguém ;-;"})
Tab1:AddParagraph({"Você está usando:", "Kakah Hub Brookhaven"})
Tab1:AddParagraph({"Team:", "KakahDev's"})

-- Rejoin Button
Tab1:AddButton({
    Name = "Rejoin",
    Callback = function()
        local TeleportService = game:GetService("TeleportService")
        TeleportService:TeleportToPlaceInstance(game.PlaceId, game.JobId, game.Players.LocalPlayer)
    end
})

---------------------------------------------------------------------------------------------------------------------------------
-- === Tab 2: Fun === --
---------------------------------------------------------------------------------------------------------------------------------
local InfiniteJumpEnabled = false
local UltimateNoclip = { Enabled = false, Connections = {}, SoccerBalls = {} }
local RunService = game:GetService("RunService")
local tcs = game:GetService("TextChatService")

-- Sliders
Tab2:AddSlider({
    Name = "Speed Player",
    Increase = 1,
    MinValue = 16,
    MaxValue = 888,
    Default = 16,
    Callback = function(Value)
        local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then humanoid.WalkSpeed = Value end
    end
})

Tab2:AddSlider({
    Name = "Jump Power",
    Increase = 1,
    MinValue = 50,
    MaxValue = 500,
    Default = 50,
    Callback = function(Value)
        local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then humanoid.JumpPower = Value end
    end
})

Tab2:AddSlider({
    Name = "Gravity",
    Increase = 1,
    MinValue = 0,
    MaxValue = 10000,
    Default = 196.2,
    Callback = function(Value)
        game.Workspace.Gravity = Value
    end
})

-- Infinite Jump
game:GetService("UserInputService").JumpRequest:Connect(function()
    if InfiniteJumpEnabled then
        local char = LocalPlayer.Character
        if char and char:FindFirstChild("Humanoid") then
            char.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
        end
    end
end)

Tab2:AddToggle({
    Name = "Infinite Jump",
    Default = false,
    Callback = function(Value)
        InfiniteJumpEnabled = Value
    end
})

-- Reset button
Tab2:AddButton({
    Name = "Reset Speed/Gravity/Jump Power ",
    Callback = function()
        local char = LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait()
        local humanoid = char:FindFirstChildOfClass("Humanoid")
        if humanoid then
            humanoid.WalkSpeed = 16
            humanoid.JumpPower = 50
        end
        game.Workspace.Gravity = 196.2
        InfiniteJumpEnabled = false
    end
})

-- Fly Universal Button (corrigido: FunTab -> Tab2)
Tab2:AddButton({
    Name = "Ativar Fly GUI",
    Description = "Carrega um GUI de fly universal",
    Callback = function()
        local success, _ = pcall(function()
            loadstring(game:HttpGet("https://rawscripts.net/raw/Universal-Script-Fly-gui-v3-30439"))()
        end)
        game.StarterGui:SetCore("SendNotification", {
            Title = success and "Sucesso" or "Erro",
            Text = success and "Fly GUI carregado!" or "Falha ao carregar o Fly GUI.",
            Duration = 5
        })
    end
})

---------------------------------------------------------------------------------------------------------------------------------
-- === Tab 3: Troll === --
---------------------------------------------------------------------------------------------------------------------------------
TrollTab:AddSection({ "SkyBox [ by Fire Hub]" })

TrollTab:AddButton({

    Name = "SkyBox [by bazuka]",

    Callback = function()

        local Players = game:GetService("Players")
        local ReplicatedStorage = game:GetService("ReplicatedStorage")
        local LocalPlayer = Players.LocalPlayer

        local Remotes = ReplicatedStorage:WaitForChild("Remotes")
        local WearRemote = Remotes:WaitForChild("Wear")
        local ChangeCharacterBody = Remotes:WaitForChild("ChangeCharacterBody")
        local WearShirtRemote = Remotes:WaitForChild("WearShirt")

        local CurrentTrack
        local BodyId = "100839513065432"
        local SkyboxActive = false
        local Humanoid, Animator

        local function SetupCharacter(char)
            Humanoid = char:WaitForChild("Humanoid")
            Animator = Humanoid:FindFirstChildOfClass("Animator")
            if not Animator then
                Animator = Instance.new("Animator", Humanoid)
            end
        end
        
        SetupCharacter(LocalPlayer.Character or LocalPlayer.CharacterAdded:Wait())
        LocalPlayer.CharacterAdded:Connect(SetupCharacter)
        local function ApplyAccessories()
        
            local Desc = Humanoid:GetAppliedDescription()
            for _, accessory in ipairs(Desc:GetAccessories(true)) do
                if accessory.AssetId then
                    pcall(function()
                        WearRemote:InvokeServer(accessory.AssetId)
                    end)
                end
            end
        end


        local function ApplyBody()
            pcall(function()
                ChangeCharacterBody:InvokeServer({
                    [1] = tonumber(BodyId),
                    [2] = nil,
                    [3] = nil,
                    [4] = nil,
                    [5] = nil,
                    [6] = nil
                })
            end)
        end

       local function PlayAnimation()
            local AnimId = "rbxassetid://101852027997337"
            local newAnim = Instance.new("Animation")
            newAnim.AnimationId = AnimId


            local newTrack
            pcall(function()
                newTrack = Animator:LoadAnimation(newAnim)
                newTrack.Priority = Enum.AnimationPriority.Action4
                newTrack:Play(0.1, 1, 1)
            end)

            CurrentTrack = newTrack
        end

        local function StopAnimation()
            if CurrentTrack then
                pcall(function()
                    CurrentTrack:Stop(0)
                end)
            end
        end

        SkyboxActive = not SkyboxActive
        if SkyboxActive then
            local id = tonumber(getgenv().SkyboxClothID or "")
            if id then
                pcall(function()
                    WearShirtRemote:InvokeServer(id)
                end)
            end
            ApplyAccessories()
            ApplyBody()
            PlayAnimation()
            print("Skybox Ù…ÙØ¹Ù‘Ù„ Ù…Ø¹ Ø§Ù„Ù…Ù„Ø§Ø¨Ø³")
        else
            StopAnimation()
            print("ØªÙ… Ø¥ÙŠÙ‚Ø§Ù Skybox")
        end
    end
})



TrollTab:AddButton({

   Name = "Remove Skybox ( Reset your Skin )",

   Callback = function()

local Remote = game:GetService("ReplicatedStorage").Remotes.ResetCharacterAppearance

firesignal(Remote.OnClientEvent)



game:GetService("ReplicatedStorage").Remotes.ResetCharacterAppearance:FireServer()



task.wait(0.5)



local player = game.Players.LocalPlayer

if player.Character and player.Character:FindFirstChild("Humanoid") then

player.Character.Humanoid.Health = 0

end

end

})




---------------------------------------------------------------------------------------------------------------------------------
-- === Tab 4: Protector === --
---------------------------------------------------------------------------------------------------------------------------------
local TabProtector = Tab3

TabProtector:AddSection("Proteção")

--// ANTI BUG
local antiBugEnabled = false

local function ProtectionBug()
    local blacklist = {
        {Name = "water", Class = "Part"},
    }

    local function neutralize(part)
        if part and part:IsA("BasePart") then
            pcall(function()
                part.Anchored = true
                part.CanCollide = false
                part.Massless = true
                part.Transparency = 1
                part:ClearAllChildren()
            end)
            pcall(function()
                part:Destroy()
            end)
        end
    end

    workspace.DescendantAdded:Connect(function(obj)
        for _, rule in ipairs(blacklist) do
            if obj.Name == rule.Name and obj.ClassName == rule.Class then
                neutralize(obj)
            end
        end
    end)

    for _, obj in ipairs(workspace:GetDescendants()) do
        for _, rule in ipairs(blacklist) do
            if obj.Name == rule.Name and obj.ClassName == rule.Class then
                neutralize(obj)
            end
        end
    end

    task.spawn(function()
        while antiBugEnabled and task.wait(0.25) do
            for _, rule in ipairs(blacklist) do
                for _, v in next, getnilinstances() do
                    if v.Name == rule.Name and v.ClassName == rule.Class then
                        neutralize(v)
                    end
                end
            end
        end
    end)

    LocalPlayer.CharacterAdded:Connect(function(char)
        local hum = char:WaitForChild("Humanoid")
        hum.Touched:Connect(function(hit)
            for _, rule in ipairs(blacklist) do
                if hit.Name == rule.Name and hit.ClassName == rule.Class then
                    neutralize(hit)
                end
            end
        end)
    end)
end

TabProtector:AddToggle({
    Name = "Anti Bug",
    Default = false,
    Callback = function(state)
        antiBugEnabled = state
        if state then
            ProtectionBug()
            print("Anti Bug ATIVADO")
        else
            print("Anti Bug DESATIVADO")
        end
    end
})

--// ANTI VOID
local antiVoidEnabled = false
TabProtector:AddToggle({
    Name = "Anti Void",
    Default = false,
    Callback = function(state)
        antiVoidEnabled = state
    end
})

RunService.Heartbeat:Connect(function()
    if antiVoidEnabled and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        local rootPart = LocalPlayer.Character.HumanoidRootPart
        if rootPart.Position.Y < -500 then
            local safeCFrame = CFrame.new(0, 100, 0)
            local rayParams = RaycastParams.new()
            rayParams.FilterDescendantsInstances = {LocalPlayer.Character}
            local result = workspace:Raycast(rootPart.Position, Vector3.new(0, 500, 0), rayParams)
            rootPart.CFrame = result and CFrame.new(result.Position + Vector3.new(0, 5, 0)) or safeCFrame
        end
    end
end)

--// ANTI SIT
local antiSitConnection = nil
local antiSitEnabled = false

TabProtector:AddToggle({
    Name = "Anti-Sit",
    Default = false,
    Callback = function(state)
        antiSitEnabled = state
        local LocalPlayer = game:GetService("Players").LocalPlayer

        if state then
            local function applyAntiSit(character)
                local humanoid = character:FindFirstChild("Humanoid")
                if humanoid then
                    humanoid.Sit = false
                    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, false)
                    if antiSitConnection then
                        antiSitConnection:Disconnect()
                    end
                    antiSitConnection = humanoid.Seated:Connect(function(isSeated)
                        if isSeated then
                            humanoid.Sit = false
                            humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
                        end
                    end)
                end
            end

            if LocalPlayer.Character then
                applyAntiSit(LocalPlayer.Character)
            end

            local characterAddedConnection
            characterAddedConnection = LocalPlayer.CharacterAdded:Connect(function(character)
                if not antiSitEnabled then
                    characterAddedConnection:Disconnect()
                    return
                end
                local humanoid = character:WaitForChild("Humanoid", 5)
                if humanoid then
                    applyAntiSit(character)
                end
            end)
        else
            if antiSitConnection then
                antiSitConnection:Disconnect()
                antiSitConnection = nil
            end
            if LocalPlayer.Character then
                local humanoid = LocalPlayer.Character:FindFirstChild("Humanoid")
                if humanoid then
                    humanoid:SetStateEnabled(Enum.HumanoidStateType.Seated, true)
                end
            end
        end
    end
})

--//  ANTI-ÁUDIO TOTAL
local antiAudioEnabled = false
local SoundService = game:GetService("SoundService")
local Workspace = game:GetService("Workspace")

local function blockAllAudio()
    local function muteSound(obj)
        if obj:IsA("Sound") then
            obj.Playing = false
            obj.Volume = 0
            obj:Destroy()
            warn("[ANTI-ÁUDIO] Som bloqueado e removido:", obj.Name)
        end
    end

    for _, descendant in pairs(Workspace:GetDescendants()) do
        muteSound(descendant)
    end
    for _, descendant in pairs(SoundService:GetDescendants()) do
        muteSound(descendant)
    end
    if LocalPlayer.Character then
        for _, descendant in pairs(LocalPlayer.Character:GetDescendants()) do
            muteSound(descendant)
        end
    end

    Workspace.DescendantAdded:Connect(function(obj)
        if antiAudioEnabled then muteSound(obj) end
    end)
    SoundService.DescendantAdded:Connect(function(obj)
        if antiAudioEnabled then muteSound(obj) end
    end)
    LocalPlayer.CharacterAdded:Connect(function(char)
        char.DescendantAdded:Connect(function(obj)
            if antiAudioEnabled then muteSound(obj) end
        end)
    end)
end

TabProtector:AddToggle({
    Name = "Anti-Áudio",
    Default = false,
    Callback = function(state)
        antiAudioEnabled = state
        if state then
            blockAllAudio()
            print(" Anti-Áudio ATIVADO: nenhum som poderá ser reproduzido.")
        else
            print(" Anti-Áudio DESATIVADO: sons liberados.")
        end
    end
})
