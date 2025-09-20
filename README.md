# SimpleAnimationService
Lightweight animation handler for Roblox with minimal setup.

Usage
lua
local AnimationService = require(path.to.module)

-- Load animation
local anim = AnimationService.LoadAnimation(character, animationId)

-- Play with optional fadeTime (default: 0.1)
anim:Play() 
anim:Play(0.5)

-- Stop with optional fadeTime (default: 0.1)
anim:Stop()
anim:Stop(0.3)

-- Check if playing
if anim:IsPlaying() then
    print("Playing")
end
Why Use It?
Simple API - just 3 main functions

Automatic animation tracking

Smooth fade in/out transitions

Lightweight - minimal performance impact

Perfect for basic animation needs without complexity.
