local part = script.Parent
local sparkles = nil
local touchCount = 0

local function createSparkles()
    if not sparkles then
        sparkles = Instance.new("Sparkles")
        sparkles.Color = Color3.new(1, 1, 0) -- Kuning
        sparkles.Parent = part
    end
end

local function removeSparkles()
    if sparkles then
        sparkles:Destroy()
        sparkles = nil
    end
end

part.Touched:Connect(function(hit)
    touchCount = touchCount + 1
    createSparkles()
end)

part.TouchEnded:Connect(function(hit)
    touchCount = touchCount - 1
    if touchCount <= 0 then
        removeSparkles()
        touchCount = 0
    end
end)
