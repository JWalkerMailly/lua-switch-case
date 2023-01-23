# Lua switch/case implementation
Simple and elegant, use as you wish.

```lua
-- ----------
-- Declare
-- ----------

-- Case will box our parameters.
case = function(value, result)
	return { cond = value, eval = result };
end

-- Switch will unbox our parameters for evaluation.
switch = function(value, ...)
	for _, v in ipairs{...} do if (value == v.cond and v.eval()) then break; end end
end

-- --------
-- Tests
-- --------

local some_var = 1; -- Change to '1', '2' or '3' for switch/case tests.

switch(some_var,

	case(1, function()
		print("Returning true inside a case statement acts like a break.");
		return true;
	end),
	
	case(2, function()
		print("No return will continue execution down switch expression tree.");
	end),
	
	case(some_var, function()
	    print("Case statement of value will act like default.");
	end)
);
```
