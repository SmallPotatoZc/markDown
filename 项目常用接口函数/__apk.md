班牌apk
---------
1. 获取关机时间
console.log(apkApi.system.getPowerOffTime())
__apk.systemGetPowerOffTime()

1. 获取开机时间
console.log(apkApi.system.getPowerWakeTime())
__apk.systemGetPowerWakeTime()

1. 设置关机时间
apkApi.system.setPowerOffTime("2017-11-08 16:20:00")
__apk.systemSetPowerOffTime("2017-11-07 19:20:00")

1. 设置开机时间
apkApi.system.setPowerWakeTime("2017-11-08 19:20:00")
__apk.systemSetPowerWakeTime("2017-11-07 19:20:00")

1. 关机
apkApi.system.shutdown()
__apk.systemShutdown()

1. 读取配置文件
apkApi.appConfig.read()
__apk.configRead()

1. 保存配置文件
apkApi.appConfig.save()
apkApi.appConfig.set()
__apk.configSave()



window.localStorage.debug="*"

console.log(new Date().toLocaleString())

apkApi.system.setPowerOffTime("2017-11-08 19:50:00")

apkApi.system.setPowerWakeTime("2017-11-08 20:00:00")