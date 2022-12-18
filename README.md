https://www.roblox.com/games/8721702870/unnamed#!/


```lua
local functions = loadstring(game:HttpGet("https://raw.githubusercontent.com/nonono100/other/main/functions"))();

```

#### functions.Build(partName, Coordinate, Orientation)

```lua
--partName - {"Wall", "Floor", "Ramp", "Door", "ShortWall", "Window", "RampLeft", "RampBack"}
--Coordinate - Vector3(x, y, z)
--Orientation - {0, 90, 180, 270}

functions.Build("Floor", Vector3.new(0, 0, 0), 0)
```


#### functions.Destroy(Part)
```lua
--used to destroy builds or clear the map

for i,v in pairs(workspace:GetDescendants()) do 
	if v:IsDescendantOf(workspace.GridContents) or v:IsDescendantOf(workspace.trees) or v:IsDescendantOf(workspace.homes) or v:IsDescendantOf(workspace["house_hills"]) then
		functions.Destroy(v)
	end
end
```
#### functions.Grid(startPostion, x, y, z)

```lua
--startPosition - Position of the starting corner in (X, Y, Z)
--x, y, z - Each axis adds blocks in that direction, [Example]: 10, 5, 10 will make a square 5 blocks tall and 10 blocks wide
--function will return an area calculated from the parameters

for i,v in pairs(functions.Grid(Vector3.new(-20, 0, -20), 40, 0, 40)) do 
	wait()
	functions.Build("Floor", v)
end
```

#### functions.buildEdges(startPosition, x, y, z)
```lua
--the same as above but with edges to make walls
--function will return coordinate and orientation example below

for i,v in pairs(functions.buildEdges(Vector3.new(-10, 0, -10), 20, 0, 20)) do 
	wait()
	functions.Build("Wall", v[1], v[2])
end

```

#### functions.buildCorners(startPostion, x, y, z)
```lua
--same as above but for corners
for i,v in pairs(functions.buildCorners(Vector3.new(-20, 0, -20), 40, 19, 40)) do 
	wait()
	functions.Build("Wall", v, 0)
	functions.Build("Wall", v, 90)
	functions.Build("Wall", v, 180)
	functions.Build("Wall", v, 270)
end

```

# EXAMPLES

![Image](https://i.ibb.co/9ym0z8j/maxresdefault.jpg)
*INVERTED PYRAMID*
```lua
local functions = loadstring(game:HttpGet("https://raw.githubusercontent.com/nonono100/other/main/functions"))();


for i,v in pairs(functions.buildEdges(Vector3.new(-10, 0, -10), 20, 10, 20)) do 
	wait()
	functions.Build("Wall", v[1], v[2])
end

for i,v in pairs(functions.buildEdges(Vector3.new(-11, 11, -11), 22, 0, 22)) do 
	wait()
	functions.Build("Floor", v[1], v[2])
end

function undoang(ang)
	if ang == 180 then
		return 0
	end
	if ang == 0 then
		return 180 
	end
	if ang == 90 then
		return 270 
	end
	if ang == 270 then
		return 90
	end
end

local c = -11
local d = 22
for i = 1,10 do 
	c = c + 1
	d = d - 2
	for i,v in pairs(functions.buildEdges(Vector3.new(c, -c, c), d, 0, d)) do 
		wait()
		functions.Build("Ramp", v[1], undoang(v[2]))
	end
end

local a = -11
local b = 22
for i = 1,10 do 
	a = a + 1
	b = b - 2
	for i,v in pairs(functions.buildCorners(Vector3.new(a, -a, a), b, 0, b)) do 
		wait()
		functions.Build("Wall", v, 0)
		functions.Build("Wall", v, 90)
		functions.Build("Wall", v, 180)
		functions.Build("Wall", v, 270)
		functions.Build("Floor", Vector3.new(v.X,v.Y + 1,v.Z), 0)
	end
end

for i,v in pairs(functions.buildEdges(Vector3.new(-12, 11, -12), 24, 0, 24)) do 
	wait()
	functions.Build("ShortWall", v[1], 270)
	functions.Build("ShortWall", v[1], 180)
	functions.Build("ShortWall", v[1], 0)
	functions.Build("ShortWall", v[1], 90)
end

```
---
![Image](https://i.ibb.co/rZ44Bxt/maxresdefault.jpg)
*DIAMOND*
```lua
local functions = loadstring(game:HttpGet("https://raw.githubusercontent.com/nonono100/other/main/functions"))();


for i,v in pairs(functions.buildCorners(Vector3.new(-10, 0, -10), 20, 10, 20)) do 
	wait()
	functions.Build("Wall", v, 0)
	functions.Build("Wall", v, 90)
	functions.Build("Wall", v, 180)
	functions.Build("Wall", v, 270)
end


function undoang(ang)
	if ang == 180 then
		return 0
	end
	if ang == 0 then
		return 180 
	end
	if ang == 90 then
		return 270 
	end
	if ang == 270 then
		return 90
	end
end

local c = -11
local d = 22
for i = 1,10 do 
	c = c + 1
	d = d - 2
	for i,v in pairs(functions.buildEdges(Vector3.new(c, -c, c), d, 0, d)) do 
		wait()
		functions.Build("Ramp", v[1], undoang(v[2]))
	end
end


local a1 = -11
local a3 = 10
local a2 = 22
for i = 1,10 do 
	a1 = a1 + 1
	a3 = a3 + 1
	a2 = a2 - 2
	for i,v in pairs(functions.buildEdges(Vector3.new(a1, a3, a1), a2, 0, a2)) do 
		wait()
		functions.Build("Ramp", v[1], v[2])
	end
end

local a = -11
local b = 22
for i = 1,10 do 
	a = a + 1
	b = b - 2
	for i,v in pairs(functions.buildCorners(Vector3.new(a, -a, a), b, 0, b)) do 
		wait()
		functions.Build("Wall", v, 0)
		functions.Build("Wall", v, 90)
		functions.Build("Wall", v, 180)
		functions.Build("Wall", v, 270)
		functions.Build("Floor", v, 0)
		functions.Build("Floor", Vector3.new(v.X,v.Y + 1,v.Z), 0)
	end
end

local b1 = -11
local b3 = 10
local b2 = 22
for i = 1,10 do 
	b1 = b1 + 1
	b3 = b3 + 1
	b2 = b2 - 2
	for i,v in pairs(functions.buildCorners(Vector3.new(b1, b3, b1), b2, 0, b2)) do 
		wait()
		functions.Build("Wall", v, 0)
		functions.Build("Wall", v, 90)
		functions.Build("Wall", v, 180)
		functions.Build("Wall", v, 270)
		functions.Build("Floor", v, 0)
		functions.Build("Floor", Vector3.new(v.X,v.Y + 1,v.Z), 0)
	end
end





```

![Image](https://i.ibb.co/rZ44Bxt/maxresdefault.jpg)
*CROSS*
```lua
local functions = loadstring(game:HttpGet("https://raw.githubusercontent.com/nonono100/other/main/functions"))();


local function reversetable(table1)
    local tabl = {}
    for i,v in pairs(table1) do 
	table.insert(tabl, v)
end
return tabl
end

-- Center
for i,v in pairs(functions.buildEdges(Vector3.new(-5, 0, -20), 3, 30, 3)) do 
	wait()
	functions.Build("Wall", v[1], v[2])
end

for i,v in pairs(functions.Grid(Vector3.new(-5, 31, -20), 3, 0, 3)) do 
	wait()
	functions.Build("Floor", v)
end

for i,v in pairs(functions.Grid(Vector3.new(-5, 2, -20), 3, 0, 3)) do 
	wait()
	functions.Build("Floor", v)
end

-- Left Side

local tabl = reversetable(functions.Grid(Vector3.new(-12, 19, -20), 6, 0, 3))
local inverse = #tabl
for i = inverse, 1, -1 do 
	wait()
	functions.Build("Floor", tabl[i])
end

for i,v in pairs(functions.buildEdges(Vector3.new(-12, 19, -20), 3, 3, 3)) do 
    	wait()
    	functions.Build("Wall", v[1], v[2])
end

for i,v in pairs(functions.buildEdges(Vector3.new(-8, 19, -20), 3, 3, 3)) do 
    	wait()
    	functions.Build("Wall", v[1], v[2])
    end

for i,v in pairs(functions.Grid(Vector3.new(-12, 23, -20), 6, 0, 3)) do 
    	wait()
    	functions.Build("Floor", v)
end

-- Right Side

for i,v in pairs(functions.Grid(Vector3.new(-1, 19, -20), 6, 0, 3)) do 
    	wait()
    	functions.Build("Floor", v)
end

for i,v in pairs(functions.Grid(Vector3.new(-1, 23, -20), 6, 0, 3)) do 
    	wait()
    	functions.Build("Floor", v)
end

for i,v in pairs(functions.buildEdges(Vector3.new(-1, 19, -20), 3, 3, 3)) do 
    	wait()
    	functions.Build("Wall", v[1], v[2])
end

for i,v in pairs(functions.buildEdges(Vector3.new(2, 19, -20), 3, 3, 3)) do 
    	wait()
    	functions.Build("Wall", v[1], v[2])
end





```
