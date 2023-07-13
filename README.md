# Signal for Playdate

[![Lua Version](https://img.shields.io/badge/Lua-5.4-yellowgreen)](https://lua.org) [![Toybox Compatible](https://img.shields.io/badge/toybox.py-compatible-brightgreen)](https://toyboxpy.io) [![Latest Version](https://img.shields.io/github/v/tag/DidierMalenfant/signal)](https://github.com/DidierMalenfant/signal/tags)

**Signal** is a **Lua** class for subscribing to keys and notifying subscribers of that key by [Dustin Mierau](https://github.com/mierau).

You can add it to your **Playdate** project by installing [**toybox.py**](https://toyboxpy.io), going to your project folder in a Terminal window and typing:

```console
toybox add Signal
toybox update
```

Then, if your code is in the `source` folder, just import the following:

```lua
import '../toyboxes/toyboxes.lua'
```

This **toybox** contains **Lua** toys for you to play with.

---

Signal creates its event bus on import. In this example we define our callback function, add it, call it a few times, and remove it:

```lua
local score = 0
local function change_score(_bind, _key, change)
   score += change
   print(score)
end

-- The second argument is the binding for the callback (first argument), useful for OOP
Signal:add("score_changed", nil, change_score)
Signal:dispatch("score_changed", 1)
Signal:dispatch("score_changed", 2)
Signal:dispatch("score_changed", -3)
Signal:remove("score_changed", change_score)
```
