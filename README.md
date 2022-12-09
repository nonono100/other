https://www.roblox.com/games/8721702870/unnamed#!/
~~~Arabic Fortnite~~~

----------------------SCRIPT EXAMPLES

local functions = loadstring(game:HttpGet("https://raw.githubusercontent.com/nonono100/other/main/functions"))();

for i,v in pairs(functions.Grid(Vector3.new(-10,0,-10), 20, 0, 20)) do 
	wait()
	functions.Build("Floor", v)
end

------------------

for i,v in pairs(functions.Grid(Vector3.new(-13,0,-13), 26, 0, 26)) do
	functions.Build("Wall", v)
	functions.Build("Wall", v, 90)
	functions.Build("Wall", v, 180)
	functions.Build("Wall", v, 270)
end

------------------

for i,v in pairs(workspace:GetDescendants()) do 
	if v:IsDescendantOf(workspace.trees) or v:IsDescendantOf(workspace.homes) or v:IsDescendantOf(workspace["house_hills"]) then
		functions.Destroy(v)
	end
end

------------------

for i,v in pairs(functions.buildEdges(Vector3.new(-10, 0, -10), 20, 0, 20)) do 
	wait()
	functions.Build("Wall", v[1], v[2])
end

