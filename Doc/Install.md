#Yuthung(月鸿)
##简介 
该项目为Unturned(未转变者)前置插件，主要对Rocket前置插件进行进一步丰富以支持更多的Api，该项目较于Rocket前置主要新增以下特点: 
1.对于玩家player而言，Yuthung中新增类YuthungPlayer以支持对角色的相关操作，并提供了一个属性以支持对玩家增加属性 
```C#
//为所有玩家创建一个Name属性，默认值为string.Empty
Y.PropertiesManager.TryAddProperty("Name",string.Empty);
//player为SDG.Unturned.Player的一个对象
YuthungPlayer yuthungPlayer = YuthungPlayer.FromPlayer(player);
//获得指定玩家对应的Name属性,其中yuthungPlayer["PropertyName"]索引器根据属性名字获得对应的属性值，返回结果为object(如果未查找到返回null)
yuthungPlayer["Name"].TryGetStructObj<string>(out var name);
``` 
2.新增Timer对象以及TimerManager管理类，并且可以同时创建多个Timer计时器对象
