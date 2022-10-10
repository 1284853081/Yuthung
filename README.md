# Yuthung
## 简介
Yuthung(月鸿)为一个用于Unturned(未转变者)的前置插件，该前置插件将会提供更多的api方便插件开发者进行开发    
## [release](https://github.com/1284853081/Yuthung/tags)
## 安装
将release中下载的压缩包解压至Unturned根目录中的Modules目录下，然后启动服务器，Yuthung将会在对应的服务器目录下生成Yuthung文件夹，使用Yuthung开发的插件只需将插件放入改文件夹中的Plugins文件夹中即可在服务器启动时完成加载
## 使用教程
以下为一个简单的插件制作例子      
1.首先打开Visual Studio创建一个.Framework的类库      
2.将安装好后的Yuthung.dll添加至引用        
3.将Unturned中的AssemblyCSharp.dll,com.rlabrecque.steamworks.net.dll,UnityEngine.dll,UnityEngine.CoreModule.dll，SDG.NetTransport.dll添加至引用      
4.创建一个类作为插件接入类，本例中使用名为Program类作为接入类     
5.实现IYuthungPlugin接口        
```C#
using Yuthung.API;
using Yuthung.Core;

namespace TestPlugin
{
    public class Program : IYuthungPlugin
    {
        //开发码，插件的唯一标识符，需要申请，一个开发码对应一个使用码
        public string DevelopedCode => "";
        //插件被加载时调用
        public void Load()
        {
            Logger.Log("Welcome to use front plugin Yuthung");
        }
        //插件卸载时调用
        public void UnLoad()
        {
            Logger.Log("Welcome to use it again");
        }
    }
}
```
> 注：开发者使用Yuthung开发插件时需申请开发码，插件制作完成后交付使用时需将开发码和插件一并交给使用者，使用者再使用开发码申请使用码并将使用码记录在配置文件中，这样服务器启动时才能加载该插件(开发码为免费申请，使用码需付费申请，申请方式 QQ:1284853081,微信：13257963263，申请需备注好，否则不通过)      
    
6.制作指令      
7.新建一个类，本例使用CommandWelcome      
8.实现IYuthungCommand接口       
```C#
using Yuthung.API;
using Yuthung.Core;
using Yuthung.Core.Enums;
using Yuthung.Unturned.UnturnedObjects;

namespace TestPlugin
{
    public class CommandWelcome : IYuthungCommand
    {
        //允许使用指令的对象
        public Caller Caller => Caller.Player;
        //指令名称，不区分大小写
        public string Name => "welcome";
        //指令前导符(前缀)
        public string Preambles => "/";
        //指令使用帮助
        public string Help => "";
        //使用指令后的调用函数
        public void Excute(IYuthungPlayer caller, string[] command)
        {
            Y.ChatManager.Say(caller as YuthungPlayer,"Welcome to use front plugin yuthung");
        }
    }
}
```
9.保存并编译，将生成的dll文件放在Yuthung目录下的Plugins目录中        
10.配置Yuthung目录中的PluginLicense.json文件，将开发码以及对应的使用码正确填写即可     
11.启动服务器加载插件        
> 以上即为一个简单插件示例，更多还请查看[帮助文档]() 待完善
