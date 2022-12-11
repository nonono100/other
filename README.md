https://www.roblox.com/games/8721702870/unnamed#!/

# functions:


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
