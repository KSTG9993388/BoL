if myHero.charName ~= "Viktor" then return end

local version = 0.01
local AUTOUPDATE = true
local SCRIPT_NAME = "SH Viktor"

local SOURCELIB_URL = "https://raw.githubusercontent.com/gbilbao/Bilbao/master/BoL1/Common/SourceLib.lua"
local SOURCELIB_PATH = LIB_PATH.."SourceLib.lua"

if FileExist(SOURCELIB_PATH) then
  require("SourceLib")
else
  DOWNLOADING_SOURCELIB = true
  DownloadFile(SOURCELIB_URL, SOURCELIB_PATH, function() print("有新版本可用") end)
end

if DOWNLOADING_SOURCELIB then print("下载所需要的库文件,请稍后...") return end

if AUTOUPDATE then
   SourceUpdater(SCRIPT_NAME, version, "raw.github.com", "/Hellsing/BoL/master/"..SCRIPT_NAME..".lua", SCRIPT_PATH .. GetCurrentEnv().FILE_NAME, "/Hellsing/BoL/master/version/"..SCRIPT_NAME..".version"):CheckUpdate()
end

local RequireI = Require("SourceLib")
RequireI:Add("vPrediction", "https://raw.githubusercontent.com/SidaBoL/Scripts/master/Common/VPrediction.lua")
RequireI:Add("SOW", "https://raw.githubusercontent.com/gbilbao/Bilbao/master/BoL1/Common/SOW.lua")
RequireI:Check()

if RequireI.downloadNeeded == true then return end
