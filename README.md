# da-cam-lock
camlock/rage/silent-aim/spoofer
loadstring([[
-- Create a LocalScript that runs in the player's PlayerGui
local player = game.Players.LocalPlayer
local userInputService = game:GetService("UserInputService")

-- Function to kick the player if they don't press R in time
local function waitForKeyPress()
    local startTime = tick()  -- Record the start time
    local keyPressed = false

    -- Function to detect key presses
    local function onKeyPress(input)
        if input.KeyCode == Enum.KeyCode.R then
            keyPressed = true
        end
    end

    -- Connect the key press event
    userInputService.InputBegan:Connect(onKeyPress)

    -- Wait for 3 seconds or until the R key is pressed
    while tick() - startTime < 3 do
        if keyPressed then
            print("R key pressed!")
            return  -- If R was pressed, exit the function and don't kick the player
        end
        wait(0.1)  -- Check every 0.1 seconds
    end

    -- If R was not pressed within 3 seconds, kick the player
    if not keyPressed then
        print("You failed to press R in time! Kicking you out of the game.")
        player:Kick("You were kicked from this experience: Mod team has BANNED you for 11 days")
    end
end

-- Call the function when the game starts
waitForKeyPress()
]])()
