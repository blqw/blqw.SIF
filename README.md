# blqw.SIF
服务接口框架

# 说明
该项目目前还处于设想阶段,我的想法是先做一个服务接口框架;  
将服务接口的功能抽象出来,业务代码直接写成类库的形式;
通过特性/配置文件/IOC或者其他形式注入服务框架,服务容器可以基于该框架适配;  
如此,即可使业务与服务容器之间解耦,切换服务容器也不需要修改业务代码; 
例如:  
同一套业务代码可以同时寄存于wcf,iis,以及各种rpc和aoc容器运行  

# 功能
1. 接口发现, 接口描述, 接口调用
1. 组件替换
1. 功能抽象


# 概念
## 1. 接口(Api)  
对应代码中的一个被`ApiAttribute`特性标注的公开实例方法
## 2. 容器(Container)  
服务与接口的集合  
接口在定义时可以设置应用到指定容器,部分容器或所有容器
服务实现`SupportContainers`属性,定义支持的容器  
容器的唯一表示是名称,且不区分大小写
## 3. 适配器(Adapter)  
用于适配指定服务器宿主程序调用指定容器中的接口和服务的行为  
一个适配器实例只能支持适配一种容器  
## 4. 请求参数(Parameter)  
对应接口的参数
## 5. 请求属性(Property)  
对应接口所在类的公开实例属性
## 6. 过滤器(Filter)  
`ApiFilterAttribute`过滤器,用于实现接口的AOP注入和短路
## 7. 服务(Service)  
对于框架中特定行为的抽象,可重写,可替换

# 更新日志
## [0.0.5] 2016.12.11
* 增加一组验证器

## [0.0.4] 2016.12.09
* 框架支持对过滤器的处理
* 框架支持对数据更该器的处理
* 框架支持对参数验证器的处理

## [0.0.3] 2016.12.08
* 删除`ApiSetting`类,改为使用拓展方法提供字典操作的支持
* 增加过滤器`ApiFilterAttribute`
* 增加数据更改器`DataModification`
* 增加Api调用上下文`ApiCallContext`
* 增加Api全局操作`ApiGlobal`

## [0.0.2] 2016.12.04
* 优化文件结构,框架拆分为2个项目,一个提供特性描述,另一个提供容器操作

## [0.0.1] 2016.12.02
* 主功能实现
