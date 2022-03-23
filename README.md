# Extended debug commands
A set of useful commands for Arma 3.

## Primary 
Disable fatigue:
```c++
player enableFatigue false;
player addEventhandler ["Respawn", {player enableFatigue false}];
```

Skip time by 5 hours:
```c++
skipTime 5;
```

Open personal arsenal:
```c++
["Open", true] spawn BIS_fnc_Arsenal;
```

Open vehicle arsenal:
```c++
["Open",true] call BIS_fnc_garage;
```

## Vehicles
Give current vehicle god mode:
```c+
vehicle player addEventHandler ["HandleDamage", {false}];
```

Fully repair the vehicle you're in:
```c++
_timeForRepair = 0; _vehicle = vehicle player; hint format ["Please wait %1 seconds for repair/flip",_timeForRepair]; sleep _timeForRepair; if (_vehicle == player) then {_vehicle = cursorTarget;}; _vehicle setfuel 1; _vehicle setdamage 0; _vehicle = nil; vehicle = this select 0; _vehicle setvectorup [0,0,1];
```

## Server
Force first person:
```c++
while {(true)} do  {  if (cameraView == "External") then  {  if ((vehicle player) == player) then  {  player switchCamera "Internal";  };  };  sleep 0.1;  };
```

## Situational
Spawns a crate with your primary weapon:
```c++
num = 15;

_crate = "Box_NATO_Support_F" createVehicle screenToWorld [0.5,0.5];
clearItemCargoGlobal _crate;
_crate addWeaponCargo [primaryWeapon player, num];
```

## Cheats
Teleport by holding left-alt & clicking on the map:
```c++
player onMapSingleClick "if (_alt) then {player setPosATL _pos}";
```

Invincibility:
```c++
player allowdamage false;
```
