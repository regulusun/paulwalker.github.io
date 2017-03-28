## 我眼中的中台 - 对总架构师组的诉求

> 其实中台是一个很大的范畴，我在本文中讲的主要是电商业务领域的中台，电商业务复杂多变，而且变化又快，而我们的系统现状是对大促支持的不错，但对快速变化的业务支持的不太好，或者说很不好，所以电商业务领域的中台已经非常迫切！  
> 另外，本文可能会存在一些理解上的偏差，还请大家指正！


## 那么，现在有哪些问题阻碍了去支持业务的快速发展
+ 沟通难，不停的开会，开了N次会后大家勉强达成一致或不欢而散
+ 有时候一些系统突然增加了很多业务，人手严重不足，需要共建（和弹性扩容缩容有点像），但系统未实现平台化，导致共建成本非常高，可能更多的时间浪费在了扯皮上
+ 评估需求慢，主要突出在交易链路，交易业务太过复杂，没人能全局把握
+ 没有人清楚目前电商业务领域有哪些能力，都是谁提供的，有没有重复的
+ 所以，不能快速支持业务，同样意味着不能快速试错
+ 系统间协同困难，这是我做动态账期项目给我的最大感触，没有之一
+ ...

问题很多，而且有些问题已经到了不得不解决的地步，否则恶性循环会一直持续下去，最终可以想象一下的结果可能是，人累死了，业务还没支持好，中台正是要解决这一系列问题而提出来的，那么中台究竟是什么？

## 什么是中台
上面我说的几点问题中，有几点说没有人能怎么怎么滴，但也确实是没有人能，因为这不是一个人所能解决的，就算有这么一个人能解决这些问题，但从稳定性的角度来讲，这会导致单点问题。所以我们需要的不是一个人，而是一组人，不过，人员总是会有变动，还是需要落地到系统或文档，规范，机制，方法论，标准等，这就引出了我们口中的中台。  
中台（Middle Office），眼下这个东东非常火，大家都在说，那这个东东到底是什么东东呢？之前哲别他们的PPT上对它的定义是这样的：“**电商业务中台由一系列业务能力标准、运行机制、业务分析方法论，配置管理和执行系统以及运营服务团队构成的体系，提供各业务方能够快速，低成本创新的能力。**”，我觉得还不够清晰，定义其实没多大问题，但感觉少了点引子和总定义，个人觉得应该在最前面加上**电商业务中台是对总架构师组的诉求，是对整个电商业务领域的解决方案的提炼**。关于诉求的定义，我很喜欢哲别他们PPT中的定义：  

	指角色的诉求，是发生商业交换的前提，相互间的诉求正好匹配，能被满足，就形成了商业交换。需求不等于诉求，需求缺乏对本质的挖掘。比如，客户要买一张凳子，这是需求，但不是诉求，这背后是有了凳子就能踩上去换坏了的灯泡。可能想到买梯子更好，但这也不是诉求。如果提供快速更换灯泡的服务，口碑良好的工人带上灯泡上门，也许客户更愿意买单，这更靠近本质。对诉求的挖掘和识别没有止境，越接近越真实，才能持续的支撑方案的良性运转。买方市场下，买家的诉求在关系中占主要地位；
	
	简单总结一下就是，“诉求不是需求，而是需求的本质”。
	

## 对总架构师组的诉求
那么，总架构师组由哪些角色组成呢？系统架构师、应用架构师、业务架构师、稳定性架构师、安全架构师、数据架构师等等这些角色应在其中，也就是说中台是在对这些角色提出需求。  
那么，中台对这个总架构师组有哪些需求或诉求呢？最终我们能看到哪些东西会在中台战略中落地呢？会有哪些挑战等着我们？

### 问题/诉求
#### 全局管控

	问题：没有人知道整个电商业务领域现在有哪些能力，怎么使用这些能力，哪些能力可以一起使用，哪些能力是互斥的，如果能力重复，是否继续共存下去  
	诉求：定义能力的定义与标准，提供一个能力注册、发现、查询等管理的机制与管理系统
	
	问题：和元数据类似，现在一些业务的身份识别也是通过打标的形式，而这个标可能并不是全局性的，可能不同的系统对同一个业务，有不同的标识，要知道这是“万恶之源”
	诉求：提供全局性的业务或应用注册管理中心，要让业务跑在大平台上，而不是一个或几个平台上
	追述：现在有些团队可能已经实现了应用注册、管理等功能，比如现在的sns体系，beehive，需要考虑一下全局统一的事
	
#### 方法论、规范及机制

	问题：业务领域不同，其中的领域对象也不同，如何去做领域对象建模，可能每个人心中所想都不太一样
	诉求：提供一套或多套领域对象建模方法论或标准，比如按领域驱动设计DDD；提供一系列成熟的案例或解决方案
	
	问题：来一个复杂点的需求，这个需求很大，比如村淘，可能很多系统都要修改，但具体不知道要改哪些系统，可能只知道一部分，很有可能漏掉了一些系统，也不知道要召集哪些人开会，当然开会成本也是相当的高（会多必定是有问题的，需要深究）
	诉求：梳理清楚整个电商业务领域链路，然后提供一种机制，输入一个需求，能通知到各链路系统owner，最终形成一个解决方案放到经典案例库上供其他同学学习、参考；
	
	问题：现在端非常的多，PC，手淘，猫客等等，如何做到多端适配
	诉求：提供多端化开发规范

#### 平台化

	问题：众所周知，现在有很多系统功能或能力是重复的，重复意味着需要用双倍的人力去维护，意味着资源的浪费，这是一个很严重的问题，很多时候，两个系统间只有少数的差别，或只因当初得不到原系统的支持，或是根本不知道对方的存在，或是...  
	诉求：定义平台化的标准，定义可以实现平台化的框架的标准，比如框架需要提供模块化、流程化、插件、扩展等功能 
	追述：平台化的标准是什么？玄难大师有个很好的比喻，如果你的业务能一键上线或下线，就接近平台化了。这里的一键上下线，不是指单纯的切换一个开关，而是要做到部署的代码里不再有和该业务相关的任何代码。
	
#### 基础构件
	
	问题：电商业务领域，业务非常复杂，业务规则更是多的数不胜数，但这些规则都是散落的，或者说应该由运营维护的，而实际上是开发在维护；
	诉求：定义业务规则的定义，提供一个统一的业务规则平台（非中心，非动态编译引擎），支持自定义DSL插件，权限，审批流程等等，最终每个业务方都可形成自己业务领域的知识库
	追述：目前内部实现的规则中心，大多是动态编译脚本引擎也不支持DSL，这不利于知识库的形成，也不利于运营人员直接介入维护业务规则
	
	问题：现在各业务系统有非常多的元数据，没有地方可以管控，有时候也不知道谁加了这些元数据，想加就加，不知道用来作什么
	诉求：建设元数据管理中心，与业务规则等平台打通
	
	问题：我的系统提供了一些服务，但不知道有哪些业务方在使用，也不知道是否有一些业务方在误用我的服务
	诉求：提供一套服务鉴权的机制
	
#### 其它
	+ 一个强大的中台，肯定少不了一些周边工具的支持
	+ 目前对云的诉求还不是特别强烈，我对云的理解也不是很多，但未来一定是云的，让外部也可以享用阿里中台的能力
	待更多同学补充...
	
总结起来，可以归结为**标准，定义，机制，平台化，方法论，规范，基础构件，“全局管控，分布运行”，解决方案**等几个关键词，这正好也和前面中台的定义大致相符，需要明确一点，前面的几个关键词都是为最后一个关键词服务的。这里讲的个别诉求，可能并不属于中台的范畴，但还是息息相关的。

## 实施中台要注意的点
#### 术语统一并且具有清晰的定义，这点至关重要
大家都在说能力，但每个人对这个词都是一样的理解么？大家的上下文是否一致？服务是能力？应用算是能力么？一种业务是能力么？对能力的基本定义又是什么？  
什么是平台？什么是平台化？如何衡量一个系统是否做到了平台化？  
同样，对于标准也是一样，要想标准能流行，必须清晰明确，不能有一点模糊性，这个有很多实例，比如4g，tcp/ip等
#### 中台的目的是为了提升研发、运营等效率
但提升效率的不一定就是中台化的东西，而且提升效率也不是中台的直接目的，而是间接目的，顺带的结果。
#### 可配置化的优先级
可配置固然重要，但其重要性远低于平台化
#### 关于重复，是否需要完全杜绝
有些系统或功能可以重复，但有些是万万不能的，比如对能力的管控，业务身份等等  
完全杜绝重复，对一个大公司来讲，几乎不可能，而且有时候也不应该杜绝，不过我们可以深究一下产生重复的缘由：
  
+ 根本不知道对方的存在
+ 知道对方的存在，然后给出了一些建议，对方未采纳，然后一怒之下搞了一套新的
+ 知道对方的存在，然后给他们提需求，对方说没时间，然后一怒之下又新搞了一套

对于第一点和第三点，有了中台后，基本可以缓解；  
重复，意味着竞争，并不一定全是坏事，很喜欢癫总对于重复的一句话：**我们要在高水平下竞争！**有些重复给公司带来了效率上的问题，有些重复给公司带来了更好的产品。

## 写在最后
正如文中开头所提到的，电商业务领域的中台已经非常迫切，我们需要定义一系列的规范及工具或框架，去实现模块化、平台化，来解决文中提到的那些问题，从而提升研发效率，推动业务快速试错，快速发展。  
中台战略的实施，平台化的思维非常重要，这应该是中台的开发者必须具备的；现在的我们经历着和当初五彩石项目类似的场景，对我们提出了更高的要求，能经历公司的一些重大技术或战略升级，我个人觉得是非常荣幸的，因为可以学到很多。
中台是一个很大的范畴，文中仅仅主讲了电商业务领域的中台，其它还会有数据领域的中台，安全领域的中台等等，不过之间只是领域不同，其它很多东西、概念都是相通的。  
最后，祝大家在新的一年里，工作顺利，健康，快乐！


## 参考资料
[共享电商TL管理沙龙第6期《电商中台策略的思考及实践》](http://www.atatech.org/articles/46118)  
[电商中台策略思考与实践视频](http://xue.alibaba-inc.com/trs/mediaDetail.htm?spm=a1z39.7477585.1998183628.97.FdLW4W&mediaUid=f9ca2393-abd7-4bc1-90aa-d5425ea48c9f)
