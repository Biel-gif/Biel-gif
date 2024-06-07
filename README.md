-- Função para ESP de frutas
function ESPFrutas()
    for i, fruta in pairs(game.Workspace.Fruits:GetChildren()) do
        local esp = Instance.new("BillboardGui", fruta)
        esp.Name = "ESP"
        esp.Size = UDim2.new(0, 100, 0, 100)
        esp.AlwaysOnTop = true

        local textLabel = Instance.new("TextLabel", esp)
        textLabel.Size = UDim2.new(1, 0, 1, 0)
        textLabel.Text = fruta.Name
        textLabel.TextColor3 = Color3.new(1, 0, 0)
        textLabel.BackgroundTransparency = 1
        textLabel.Font = Enum.Font.SourceSans
    end
end

-- Função para ESP de jogadores
function ESPJogadores()
    for _, jogador in pairs(game.Players:GetPlayers()) do
        if jogador ~= game.Players.LocalPlayer then
            local char = jogador.Character
            if char then
                local esp = Instance.new("BillboardGui", char)
                esp.Name = "ESP"
                esp.Size = UDim2.new(0, 100, 0, 100)
                esp.AlwaysOnTop = true

                local textLabel = Instance.new("TextLabel", esp)
                textLabel.Size = UDim2.new(1, 0, 1, 0)
                textLabel.Text = jogador.Name
                textLabel.TextColor3 = Color3.new(0, 1, 0)
                textLabel.BackgroundTransparency = 1
                textLabel.Font = Enum.Font.SourceSans
            end
        end
    end
end

-- Função de Auto Farm
function AutoFarm()
    while wait(1) do
        local player = game.Players.LocalPlayer
        local char = player.Character
        if char and char:FindFirstChild("HumanoidRootPart") then
            for _, mob in pairs(game.Workspace.Mobs:GetChildren()) do
                if mob:FindFirstChild("HumanoidRootPart") then
                    char.HumanoidRootPart.CFrame = mob.HumanoidRootPart.CFrame * CFrame.new(0, 5, 0)
                    -- Ataque o mob aqui
                    wait(1)
                end
            end
        end
    end
end

-- Função de Auto Trial V4
function AutoTrialV4()
    while wait(1) do
        -- Supondo que os trials estejam em game.Workspace.Trials
        for _, trial in pairs(game.Workspace.Trials:GetChildren()) do
            if trial:FindFirstChild("Entrance") then
                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = trial.Entrance.CFrame
                -- Iniciar o trial aqui
                wait(1)
            end
        end
    end
end

-- Chamar as funções
ESPFrutas()
ESPJogadores()
spawn(AutoFarm)
spawn(AutoTrialV4)
