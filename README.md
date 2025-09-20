# SimpleAnimationService

A lightweight and easy-to-use animation handler for Roblox that simplifies loading, playing, and stopping animations.

Features
Simple API: Easy-to-understand functions for animation management

Smooth Transitions: Built-in fade in/out functionality

Animation Tracking: Keeps track of all active animations

Flexible Control: Adjust weight and speed of animations on the fly

State Management: Check if an animation is currently playing

Installation
Place the SimpleAnimationService module in ReplicatedStorage or another appropriate location:

lua
local SimpleAnimationService = require(game.ReplicatedStorage.SimpleAnimationService)
Usage
Loading an Animation
lua
local character = game.Players.LocalPlayer.Character
local animationId = 123456789  -- Your animation ID here

local animation = SimpleAnimationService.LoadAnimation(character, animationId)
Playing an Animation
lua
-- Play with default parameters (0.1s fade, weight 1, speed 1)
animation:Play()

-- Play with custom parameters
animation:Play(0.5, 0.8, 1.2)  -- fadeTime, weight, speed
Stopping an Animation
lua
-- Stop with default fade time (0.1 seconds)
animation:Stop()

-- Stop with custom fade time
animation:Stop(0.5)  -- 0.5 second fade out
Adjusting Animation Properties
lua
-- Adjust weight and/or speed during playback
animation:Adjust(0.5, 0.8)  -- weight, speed
Checking Animation State
lua
if animation:IsPlaying() then
    print("Animation is currently playing")
else
    print("Animation is not playing")
end
Getting All Active Animations
lua
local activeAnimations = SimpleAnimationService.GetStorage()
for anim, _ in pairs(activeAnimations) do
    print("Active animation found")
end
API Reference
LoadAnimation(character, animationId)
Loads an animation for the specified character.

character: The Model instance representing the character

animationId: The numeric ID of the animation to load

Returns: An animation object with control methods

Animation Object Methods
Play(fadeTime, weight, speed)
Plays the animation with optional parameters.

fadeTime: (Optional) Fade-in time in seconds (default: 0.1)

weight: (Optional) Animation weight (default: 1)

speed: (Optional) Playback speed (default: 1)

Stop(fadeTime)
Stops the animation with optional fade-out.

fadeTime: (Optional) Fade-out time in seconds (default: 0.1)

Adjust(weight, speed)
Adjusts animation properties during playback.

weight: (Optional) New weight value

speed: (Optional) New speed value

IsPlaying()
Returns whether the animation is currently playing.

Returns: Boolean indicating playback status

GetTrack()
Returns the underlying AnimationTrack object.

Returns: AnimationTrack instance

GetStorage()
Returns a table of all active animations.

Returns: Table containing all currently playing animations

Example
lua
local SimpleAnimationService = require(game.ReplicatedStorage.SimpleAnimationService)

local function setupAnimations(player)
    player.CharacterAdded:Connect(function(character)
        local humanoid = character:WaitForChild("Humanoid")
        
        -- Load animations
        local walkAnim = SimpleAnimationService.LoadAnimation(character, 123456789)
        local jumpAnim = SimpleAnimationService.LoadAnimation(character, 987654321)
        
        -- Play walk animation when moving
        humanoid.Running:Connect(function(speed)
            if speed > 1 and not jumpAnim:IsPlaying() then
                walkAnim:Play(0.2)
            else
                walkAnim:Stop(0.2)
            end
        end)
        
        -- Play jump animation when jumping
        humanoid.Jumping:Connect(function()
            jumpAnim:Play(0.1)
            wait(0.5)
            jumpAnim:Stop(0.2)
        end)
    end)
end

game.Players.PlayerAdded:Connect(setupAnimations)
Why Use SimpleAnimationService?
Simplifies Animation Management: Reduces boilerplate code for animation handling

Prevents Animation Conflicts: Built-in tracking helps manage multiple animations

Smooth Transitions: Easy fade in/out prevents jarring animation transitions

Lightweight: Minimal performance overhead compared to more complex solutions

Easy to Learn: Intuitive API that's perfect for beginners and sufficient for most use cases

License
MIT License - feel free to use this in your projects!


@Made by ZEP
