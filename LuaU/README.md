# Demon Library - Comprehensive Roblox Development Utility

A powerful and extensive utility library for Roblox development written in LuaU. **Demon Library** provides 100+ functions to streamline your game development workflow.

**Version:** 2.0.0  
**Author:** XxDEMONxX-lab  
**Library Name:** Demon Library

## 📋 Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
  - [Table Utilities](#table-utilities)
  - [Math Utilities](#math-utilities)
  - [String Utilities](#string-utilities)
  - [Roblox Instance Utilities](#roblox-instance-utilities)
  - [Signal/Event System](#signalevent-system)
  - [Debounce & Throttle](#debounce--throttle)
  - [Color Utilities](#color-utilities)
  - [Array Utilities](#array-utilities)
  - [Physics & Geometry](#physics--geometry)
  - [Time & Date](#time--date)
  - [Type Checking](#type-checking)
  - [Performance & Debugging](#performance--debugging)
  - [Validation](#validation)

## 🚀 Installation

1. Copy the `LuaU` folder into your Roblox project
2. Import the library in your scripts:

```lua
local DemonLibrary = require(script.Parent.LuaU)
```

## 📖 Usage

### Basic Example

```lua
local DemonLibrary = require(script.Parent.LuaU)

-- Clamp a number between 0 and 100
local value = DemonLibrary.Clamp(150, 0, 100) -- Returns 100

-- Split a string
local parts = DemonLibrary.StrSplit("hello,world,roblox", ",")
-- Returns {"hello", "world", "roblox"}

-- Merge tables
local merged = DemonLibrary.TableMerge({a = 1}, {b = 2})
-- Returns {a = 1, b = 2}
```

## 📚 API Reference

### Table Utilities

#### TableMerge(table1, table2)
Merges two tables together.
```lua
local result = DemonLibrary.TableMerge({a = 1}, {b = 2})
-- Returns {a = 1, b = 2}
```

#### TableClone(tbl)
Deep clones a table recursively.
```lua
local original = {a = 1, b = {c = 2}}
local clone = DemonLibrary.TableClone(original)
```

#### TableFilter(tbl, predicate)
Filters a table based on a condition.
```lua
local numbers = {1, 2, 3, 4, 5}
local evenNumbers = DemonLibrary.TableFilter(numbers, function(n) return n % 2 == 0 end)
-- Returns {2, 4}
```

#### TableMap(tbl, mapper)
Maps and transforms array elements.
```lua
local numbers = {1, 2, 3}
local doubled = DemonLibrary.TableMap(numbers, function(n) return n * 2 end)
-- Returns {2, 4, 6}
```

#### TableReduce(tbl, accumulator, reducer)
Reduces table to single value.
```lua
local numbers = {1, 2, 3, 4}
local sum = DemonLibrary.TableReduce(numbers, 0, function(acc, val) return acc + val end)
-- Returns 10
```

#### TableFind(tbl, predicate)
Finds first element matching condition.
```lua
local found = DemonLibrary.TableFind({1, 2, 3, 4}, function(n) return n > 2 end)
-- Returns 3
```

#### TableFlatten(tbl, depth)
Flattens nested tables.
```lua
local nested = {1, {2, 3}, {4, {5}}}
local flat = DemonLibrary.TableFlatten(nested)
-- Returns {1, 2, 3, 4, 5}
```

#### TableSort(tbl, key)
Sorts table by key or custom function.
```lua
local items = {{name = "B"}, {name = "A"}}
local sorted = DemonLibrary.TableSort(items, "name")
```

#### TableInvert(tbl)
Inverts table keys and values.
```lua
local mapping = {red = 1, blue = 2}
local inverted = DemonLibrary.TableInvert(mapping)
-- Returns {1 = "red", 2 = "blue"}
```

#### TableMergeMultiple(tables)
Merges multiple tables.
```lua
local merged = DemonLibrary.TableMergeMultiple({{a=1}, {b=2}, {c=3}})
-- Returns {a=1, b=2, c=3}
```

#### TableGetKeys(tbl) / TableGetValues(tbl)
Gets all keys or values from table.
```lua
local keys = DemonLibrary.TableGetKeys({a = 1, b = 2})
-- Returns {"a", "b"}
```

### Math Utilities

#### Clamp(value, min, max)
Clamps a number between min and max.
```lua
local clamped = DemonLibrary.Clamp(150, 0, 100) -- Returns 100
```

#### Lerp(a, b, t)
Linear interpolation.
```lua
local value = DemonLibrary.Lerp(0, 100, 0.5) -- Returns 50
```

#### Round(num, decimals)
Rounds to decimal place.
```lua
local rounded = DemonLibrary.Round(3.14159, 2) -- Returns 3.14
```

#### Distance(pos1, pos2)
Distance between two Vector3 positions.
```lua
local dist = DemonLibrary.Distance(Vector3.new(0, 0, 0), Vector3.new(3, 4, 0)) -- Returns 5
```

#### AngleBetween(v1, v2)
Angle between vectors in degrees.
```lua
local angle = DemonLibrary.AngleBetween(Vector3.new(1, 0, 0), Vector3.new(0, 1, 0)) -- Returns 90
```

#### RandomInt(min, max) / RandomFloat(min, max)
Generate random numbers.
```lua
local randInt = DemonLibrary.RandomInt(1, 10)
local randFloat = DemonLibrary.RandomFloat(0, 1)
```

#### Abs(num) / Sign(num)
Absolute value and sign.
```lua
local abs = DemonLibrary.Abs(-5) -- Returns 5
local sign = DemonLibrary.Sign(-10) -- Returns -1
```

#### Pow(base, exponent) / Sqrt(num)
Power and square root.
```lua
local power = DemonLibrary.Pow(2, 3) -- Returns 8
local root = DemonLibrary.Sqrt(16) -- Returns 4
```

#### Map(value, inMin, inMax, outMin, outMax)
Maps value between ranges.
```lua
local mapped = DemonLibrary.Map(5, 0, 10, 0, 100) -- Returns 50
```

#### SmoothStep(t) / SmootherStep(t)
Easing functions.
```lua
local eased = DemonLibrary.SmoothStep(0.5) -- Smooth interpolation
```

#### Factorial(n) / IsEven(n) / IsOdd(n)
Math operations.
```lua
local fact = DemonLibrary.Factorial(5) -- Returns 120
```

### String Utilities

#### StrSplit(str, delimiter)
Split string by delimiter.
```lua
local parts = DemonLibrary.StrSplit("a,b,c", ",") -- Returns {"a", "b", "c"}
```

#### StrTrim(str)
Trim whitespace.
```lua
local trimmed = DemonLibrary.StrTrim("  hello  ") -- Returns "hello"
```

#### StrStartsWith(str, prefix) / StrEndsWith(str, suffix)
Check string prefix/suffix.
```lua
local starts = DemonLibrary.StrStartsWith("hello", "hel") -- Returns true
```

#### StrUpper(str) / StrLower(str)
Case conversion.
```lua
local upper = DemonLibrary.StrUpper("hello") -- Returns "HELLO"
```

#### StrReverse(str)
Reverse string.
```lua
local rev = DemonLibrary.StrReverse("hello") -- Returns "olleh"
```

#### StrReplace(str, find, replace)
Replace all occurrences.
```lua
local replaced = DemonLibrary.StrReplace("hello world", "l", "L") -- Returns "heLLo worLd"
```

#### StrRepeat(str, count)
Repeat string.
```lua
local repeated = DemonLibrary.StrRepeat("ab", 3) -- Returns "ababab"
```

#### StrContains(str, substring)
Check if contains substring.
```lua
local has = DemonLibrary.StrContains("hello world", "world") -- Returns true
```

#### StrCapitalize(str) / StrTitleCase(str)
Capitalize strings.
```lua
local cap = DemonLibrary.StrCapitalize("hello") -- Returns "Hello"
local title = DemonLibrary.StrTitleCase("hello world") -- Returns "Hello World"
```

#### StrFormat(template, args)
Template string formatting.
```lua
local formatted = DemonLibrary.StrFormat("Hello {0}, you have {1} points", {"Player", 100})
-- Returns "Hello Player, you have 100 points"
```

### Roblox Instance Utilities

#### FindDescendantByName(parent, name)
Find descendant by name.
```lua
local part = DemonLibrary.FindDescendantByName(workspace, "MyPart")
```

#### FindDescendantsByName(parent, name)
Find all descendants by name.
```lua
local parts = DemonLibrary.FindDescendantsByName(workspace, "Platform")
```

#### FindDescendantsByClass(parent, class)
Find descendants by class.
```lua
local parts = DemonLibrary.FindDescendantsByClass(workspace, "Part")
```

#### GetProperty(instance, property, default)
Safely get property.
```lua
local transparency = DemonLibrary.GetProperty(part, "Transparency", 0)
```

#### SetProperty(instance, property, value)
Safely set property.
```lua
DemonLibrary.SetProperty(part, "Transparency", 0.5)
```

#### CreateInstance(class, properties, parent)
Create instance with properties.
```lua
local part = DemonLibrary.CreateInstance("Part", {BrickColor = BrickColor.new("Red"), Size = Vector3.new(4, 1, 2)}, workspace)
```

#### GetInstancePath(instance) / FindByPath(root, path)
Get/find instance by path.
```lua
local path = DemonLibrary.GetInstancePath(part) -- Returns "Workspace/Part"
local found = DemonLibrary.FindByPath(workspace, "Part/Mesh")
```

#### ConnectMultipleEvents(instances, eventName, callback)
Connect to multiple events.
```lua
local connections = DemonLibrary.ConnectMultipleEvents(parts, "Touched", function(hit) print("Touched!") end)
```

### Signal/Event System

#### Signal()
Create custom signal.
```lua
local signal = DemonLibrary.Signal()
signal:Connect(function(...) print("Fired!") end)
signal:Fire("data")
local data = signal:Wait()
```

### Debounce & Throttle

#### Debounce(func, delay)
Debounced function (waits for inactivity).
```lua
local debounced = DemonLibrary.Debounce(function() print("Called!") end, 0.5)
```

#### Throttle(func, delay)
Throttled function (limits call rate).
```lua
local throttled = DemonLibrary.Throttle(function() print("Called!") end, 1)
```

#### Once(func)
Function that executes only once.
```lua
local once = DemonLibrary.Once(function() print("Only once!") end)
```

### Color Utilities

#### RGBToColor3(r, g, b)
Convert RGB to Color3.
```lua
local color = DemonLibrary.RGBToColor3(255, 0, 0) -- Red
```

#### HexToColor3(hex)
Convert hex to Color3.
```lua
local color = DemonLibrary.HexToColor3("#FF0000") -- Red
```

#### LerpColor(color1, color2, t)
Interpolate between colors.
```lua
local color = DemonLibrary.LerpColor(Color3.new(1, 0, 0), Color3.new(0, 0, 1), 0.5)
```

#### Color3ToRGB(color)
Convert Color3 to RGB.
```lua
local r, g, b = DemonLibrary.Color3ToRGB(Color3.new(1, 0, 0))
```

#### RandomColor() / InvertColor(color)
Random and inverted colors.
```lua
local randColor = DemonLibrary.RandomColor()
local inverted = DemonLibrary.InvertColor(Color3.new(1, 0, 0))
```

### Array Utilities

#### ReverseArray(arr)
Reverse array.
```lua
local reversed = DemonLibrary.ReverseArray({1, 2, 3, 4, 5}) -- Returns {5, 4, 3, 2, 1}
```

#### ShuffleArray(arr)
Shuffle array randomly.
```lua
local shuffled = DemonLibrary.ShuffleArray({1, 2, 3, 4, 5})
```

#### ArraySlice(arr, n) / ArrayFirst(arr) / ArrayLast(arr)
Get array slices and ends.
```lua
local first = DemonLibrary.ArrayFirst({1, 2, 3}) -- Returns 1
local last = DemonLibrary.ArrayLast({1, 2, 3}) -- Returns 3
```

#### ArrayConcat(...) / ArrayUnique(arr)
Combine arrays and remove duplicates.
```lua
local concat = DemonLibrary.ArrayConcat({1, 2}, {3, 4}) -- Returns {1, 2, 3, 4}
local unique = DemonLibrary.ArrayUnique({1, 2, 2, 3}) -- Returns {1, 2, 3}
```

#### ArrayRange(start, finish, step)
Create range array.
```lua
local range = DemonLibrary.ArrayRange(1, 10, 2) -- Returns {1, 3, 5, 7, 9}
```

#### ArraySample(arr, count)
Get random elements.
```lua
local sample = DemonLibrary.ArraySample({1, 2, 3, 4, 5}, 2)
```

### Physics & Geometry

#### IsPointInPart(point, part)
Check if point is in part.
```lua
local isInside = DemonLibrary.IsPointInPart(Vector3.new(0, 0, 0), part)
```

#### Raycast(origin, direction, maxDistance)
Cast ray.
```lua
local hit = DemonLibrary.Raycast(Vector3.new(0, 0, 0), Vector3.new(0, -1, 0), 1000)
```

#### GetClosestPart(position, parts)
Find closest part.
```lua
local closest, distance = DemonLibrary.GetClosestPart(position, parts)
```

### Time & Date

#### FormatTime(seconds)
Format time as MM:SS.
```lua
local formatted = DemonLibrary.FormatTime(65) -- Returns "01:05"
```

#### GetElapsedTime(mark)
Get elapsed milliseconds.
```lua
local start = tick()
task.wait(1)
local elapsed = DemonLibrary.GetElapsedTime(start) -- Returns ~1000
```

#### WaitUntil(condition, timeout)
Wait for condition.
```lua
local success = DemonLibrary.WaitUntil(function() return player.Health == 0 end, 5)
```

### Type Checking

#### IsNumber(value) / IsString(value) / IsTable(value) / IsVector3(value) / IsColor3(value) / IsInstance(value) / IsBoolean(value) / IsFunction(value)
Check value types.
```lua
if DemonLibrary.IsNumber(value) then print("It's a number!") end
```

### Performance & Debugging

#### BenchmarkStart(name) / BenchmarkEnd(name, startTime)
Benchmark code.
```lua
local start = DemonLibrary.BenchmarkStart("MyFunction")
-- ... code to benchmark ...
DemonLibrary.BenchmarkEnd("MyFunction", start)
```

#### PrintTable(tbl)
Print table nicely.
```lua
DemonLibrary.PrintTable({a = 1, b = {c = 2}})
```

#### Log(message, level)
Log with timestamp.
```lua
DemonLibrary.Log("Game started", "INFO")
DemonLibrary.Log("Warning!", "WARN")
```

#### GetMemoryInfo()
Get memory usage.
```lua
local info = DemonLibrary.GetMemoryInfo()
print("Memory used:", info.usedMB, "MB")
```

### Validation

#### ValidateRequired(tbl, required)
Validate required fields.
```lua
local valid, err = DemonLibrary.ValidateRequired({a = 1}, {"a", "b"})
if not valid then print(err) end
```

#### ValidateType(value, expectedType)
Validate value type.
```lua
if DemonLibrary.ValidateType(value, "number") then print("Valid!") end
```

#### ValidateRange(value, min, max)
Validate number range.
```lua
if DemonLibrary.ValidateRange(score, 0, 100) then print("Valid score!") end
```

## 📝 License

This library is part of the ZHX-ML-script project by XxDEMONxX-lab.

## 🤝 Contributing

Feel free to submit issues and enhancement requests!
