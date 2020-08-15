总结报告：

一.个人针对MineRL项目的理解：

  MineRL项目目的在于促进模仿学习方法的发展，模仿学习可以通过模仿人类或者其他AI算法完成任务，提升学习效率。MineRL的主要目的是利用模仿实现自举学习，让AI不再需要耗费大量时间来探索游戏内的环境，发掘符合第一性原理的可能性，而是利用人类已有的知识经验。但是，模仿学习也有部分局限性，一旦它倾向于给出在训练样本中见过的解决方案，这种训练方式会让AI失去灵活性。

二.MineRL的项目要求：

  需要在4天时间内用不超过800万部计算来训练AI以找到Minecraft游戏中的钻石。提交的内容必须在不依赖于人类领域知识的情况下训练机器学习模型。参与者可以使用提供的人类演示的MineRL-v0数据集，但不能使用外部数据集。

三.关于Minecraft（我的世界）如何获取钻石的流程：

![Alt text](https://github.com/Kether-Jechidah/HW9/blob/master/%E7%90%86%E8%AE%BA%E5%85%AC%E5%BC%8F%E5%8F%8A%E7%AE%97%E6%B3%95%E6%B5%81%E7%A8%8B/%E5%AF%BB%E6%89%BE%E9%92%BB%E7%9F%B3%E6%B5%81%E7%A8%8B.png)
   
   以前本人并未接触过Minecraft这款游戏，为了这次作业特别游玩了十几小时。通过个人游戏经验可知，在游戏中随即重生的情况下，要获得钻石需要经过以下步骤：
        1.徒手采集木头
        2.制造工作台
        3.通过工作台制造木镐
        4.使用木镐采集石材
        5.通过工具台制作石镐
        6.采集铁矿及煤矿
        7.制造熔炉
        8.将铁矿作为原料，煤矿作为燃料放入熔炉，将铁矿练成铁锭
        9.通过工作台制作铁镐
        10.在水平面下0-15层挖掘以寻找钻石矿
        11.采集钻石

四.运行环境搭建及遇到的困难与自身总结：
    本次作业运行环境搭建难度远远大于个人预期，究其原因还是个人对服务器使用不熟悉，运行环境搭建不熟练，使用各模块版本不匹配等原因造成的。除了个人原因，本次作业还遇到了Amazon服务器下载数据极慢且下载失败的问题，Redis编译错误等问题。最终通过陈齐斌老师微信答疑与助教Q&A档案解决，在此感谢各位老师！



五.PPO算法的个人理解：
    PPO算法是一种新型的Policy Gradient算法，Policy Gradient算法对步长十分敏感，但是又难以选择合适的步长，在训练过程中新旧策略的变化差异如果过大则不利于学习。PPO算法提出了新的目标函数可以再多个训练步骤实现小批量的更新，解决了Policy Gradient算法步长难以确定的问题。
    PPO有三点主要知识点：
        1.用网络求解连续动作问题。
        2.进行N步更新。
        3.重要性采样及PPO网络的更新学习。       
    以下为PPO算法流程实现图：
    
![Alt text](https://github.com/Kether-Jechidah/HW9/blob/master/%E7%90%86%E8%AE%BA%E5%85%AC%E5%BC%8F%E5%8F%8A%E7%AE%97%E6%B3%95%E6%B5%81%E7%A8%8B/PPO%E7%AE%97%E6%B3%95%E6%B5%81%E7%A8%8B%E5%9B%BE.png)

六.Rainbow模型的个人理解：
    Rainbow将深度Q神经网络（DQN）中异策略算法Q-Learning与卷积神经网络作为函数逼近器相结合，将原始像素映射到动作价值函数里。价值分布强化学习提出了一种通过 C51 算法预测可能值函数 bin 上的分布技术。Rainbow 将上述所有技术组合在单一的异策略算法中，用以实现 Atari 基准的最新 Sample Efficiency。此外，Rainbow 还使用了多步回报。 
    以下为Rainbow模型与不同模型的得分差异：
    
![Alt text](https://github.com/Kether-Jechidah/HW9/blob/master/%E7%90%86%E8%AE%BA%E5%85%AC%E5%BC%8F%E5%8F%8A%E7%AE%97%E6%B3%95%E6%B5%81%E7%A8%8B/Rainbow%E7%AD%89%E6%A8%A1%E5%9E%8B%E5%BE%97%E5%88%86.png)

七.运行结果及竞赛官方实验结果：

    ![Alt text](https://github.com/Kether-Jechidah/HW9/blob/master/Result/PPO_Snapshot_Result.png)
   
   竞赛官方结果为：
    MineRLNavigate-v0.txt Rainbow: 
        best_score: 13.0 +- 33.63034344160047 ("+-" denotes standard deviation) 
        PPO: best_score: 8.0 +- 27.129319932501073 ("+-" denotes standard deviation) 
        DDDQN: best_score: 4.0 +- 19.595917942265423 ("+-" denotes standard deviation)

    MineRLTreechop-v0.txt Rainbow:
        best_score: 62.44 +- 2.7434285119171578 ("+-" denotes standard deviation) 
        PPO: best_score: 56.31 +- 8.306256677950662 ("+-" denotes standard deviation) 
        DDDQN: best_score: 5.28 +- 2.867333255831976 ("+-" denotes standard deviation)

    MineRLNavigateDense-v0.txt Rainbow: 
        best_score: 66.89166902255266 +- 41.23925514895555 ("+-" denotes standard deviation)            
        PPO: best_score: 87.82769563049078 +- 59.455629216295144 ("+-" denotes standard deviation) 
        DDDQN: best_score: 59.134177452623845 +- 52.43237430511946 ("+-" denotes standard deviation)

八.个人总结：

    本次作业未能找到队友一起且做完成，主要由于平时未在社区内积极交流，以至于组队时问了2位同学都表示已有队伍。由于交流沟通不到位，导致作业中很多头痛的问题不得不硬着头皮攻克。以后需要多多加强沟通交流，善于团队协作。
    最后，感谢指导老师给予的指导，在微信群等交流渠道不厌其烦的答疑。同时感谢老师的批阅，不足之处，请多多指正，谢谢！

九.参考文献：
    1.MineRL A Large-Scale Dataset of Minecraft Demonstrations
    2.NeurIPS 2019 Competition The MineRL Competition on Sample Efficient Reinforcement Learning using Human Priors
    3.Rainbow Combining Improvements in Deep Reinforcement Learning
    4.Rainbow Combining Improvements in Deep Reinforcement Learning
