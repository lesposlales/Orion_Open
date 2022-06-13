# Orion Open library Documentation
This library is an exact one to one replica of the original Orion Library found here: https://github.com/shlexware/Orion

All documentation from the original library still apply, but the following has been removed from this verison:

```
Removed Color Picker
Removed Premium Features
Removed Config Features
Removed Init() Function (Previously required)
Removed Flags
```

Other then the above mentioned features, everything else is replicated to the best of my ability.

## Loadstring:

This is the loadstring you must use for the OrionLib variable found in the original documentation:
```lua
local OrionLib = loadstring(game:HttpGet(('https://pastebin.com/raw/psGx1Bcn')))()
```

## Added Features:
The following has been added to the new version of the library:

```
Added DestroyObject() Function for Buttons, Toggles, Sliders, Labels, Paragraphs, TextBoxes, KeyBinds, Dropdowns
Added optional AutoRun Argument for Toggles, Sliders, Dropdowns
Added Self Parameter for Buttons, Toggles, Sliders, TextBoxes, KeyBinds, Dropdowns
Added PostWebhook Function
```

## DestroyObject Function:
The DestroyObject Function is useful for destroying Buttons, Toggles, etc.
Here is an example of this Function:
```lua
local Button = Tab:AddButton({
	Name = "Button!",
	Callback = function()
      	    print("Pressed")
  	end   
})

Button:DestroyObject() --Will destroy the button.
```
In the example above the button will be destroyed after its created.

## AutoRun Argument:
The AutoRun argument is useful for automatically running the Callback function as soon as the object is created.
Example:
```lua
Tab:AddToggle({
	Name = "This is a toggle!",
	Default = false,
	Callback = function(Value)
		print(Value)
	end,
  AutoRun = true
})
```
In the example above, as soon as the Toggle is created, it will run the Callback function once.

## Self Parameter:

The Self Parameter is useful when you want to use a Player Input's own Functions.
For Example:

Say you have a button and when it's Callback Function is ran, it will destroy itself. 
For this situation you can use the Self Parameter like this:
```lua
Tab:AddButton({
	Name = "Button!",
	Callback = function(Self)
      	Self:DestroyObject()
  	end    
})
```
So when you press the button it will destroy itself!

This is just one application of the Self Parameter. You could also do something like this:
```lua
Tab:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 20,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "bananas",
	Callback = function(Value, Self)
	    if Value == 8 then
            	Self:Set(1)
            end
	end
})
```
In this example, if the value of the slider is 8 then the slider value will be set to 1.

## PostWebhook Function:

The PostWebhook Function is useful for sending HTTP POST Requests to Discord Webhooks.
Here is an Example:
```lua
local Color = {Red = "16711680", Orange = "16746496", Yellow = "15728448", Green = "5887061", Blue = "2383615", Purple = "12255487"}

OrionLib:PostWebhook({
    URL = "DISCORD WEBHOOK URL",
    Title = "My Webhook",
    Content = "Hello!",
    Color = Color.Red
})

--[[
URL = <string> - The URL of your Discord Webhook.
Title = <string> - The Title of your Webhook.
Content = <string> - The Content of your Webhook
Color = <number> - The Color of your Webhook (Decimal Color Value)
]]
```

The following will send a Discord Embed message to your Webhook.

The Color Table makes it easier for you to select your Color, but not required.

String escaping such as the \n escape can be used for content of your Webhook.
