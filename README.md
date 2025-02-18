local player = game.Players.LocalPlayer
local chatService = game:GetService("Players")

local attackPower = 10  -- Начальная сила

chatService.PlayerChatted:Connect(function(player, message)
    if player == game.Players.LocalPlayer then
        local args = string.split(message, " ")
        if args[1] == ";power" then
            attackPower = tonumber(args[2]) or 10
            print("Сила удара установлена на:", attackPower)
        end
    end
end)

-- Пример удара
local function punch(target)
    if target and target:FindFirstChildOfClass("Humanoid") then
        target:FindFirstChildOfClass("Humanoid"):TakeDamage(attackPower)
        print("Удар! Нанесено:", attackPower, "урона")
    end
end
