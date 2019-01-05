  construct2可以说为编程零基础的小白提供了一个当游戏制作者的机会。每个人心中都有都会有一个“游戏梦”，想要了解游戏制作的幕后操作，接下来介绍本人第一次制作一个样本游戏的盗版低配版的过程。
 
  插入对象 

    首先我们来为游戏添加背景。使用Construct 2里的Tiled Background对象（平铺壁纸相信大家都很熟悉。通俗点，就是一个图片可以向四方重复粘贴，和网页背景图类似，能防止游戏在加载时因图片太大而减慢速度）背景创建完毕，你可以按CTRL+鼠标滚轮来放大缩小，或者点击view菜单-zoom命令来查看整体效果，你也可以按住space空格键，或者按下鼠标中键，来平移画布，很类似PS的操作。你也可以按CTRL+0或者view菜单-zoom to 100%命令来恢复画布1：1的视图模式。 

添加层 

    接下来，我们来添加更多的对象。首先我们先去把背景瓦片对象锁定了，这样才不会被我们再次选中，和PS,FL里的锁定一样。 
    画布由多个层组成，我们可以在不同的层放置不同的对象，可以通过调整层的上下顺序来调整对象的前后显示，层可以被隐藏或者锁定，平滚特效等。背景瓦片放置于最底层，其他对象如玩家，怪物，NPC等放置在上面的几层。 
    我们可以通过Layers tab来管理层，和Project bar工程面板在一个选项卡中。 

游戏对象 

    是时候来添加游戏对象了，如玩家角色，怪物角色，子弹，游戏特效等。下面是本例中要用的图片： 

玩家: 
Player texture 
怪物: 
Monster texture 
子弹: 
Bullet texture 
爆炸特效: 
Explosion texture 

在CT2中，游戏中这些对象，我们将采用sprite（RPG中好些人称为精灵，在flash里成为元件）对象来置入。该对象用来显示图片（纹理，图像设计专业说法，在CT2里可以就认为图片），还可以移动，旋转或缩放。 

接下来依次插入上面的几个对象，插入过程如下，和上面的操作一样，大致如下： 
1、双击插入新对象 
2、双击选择Sprite对象 
3、当鼠标变成十字，在画布中点击 
4、弹出对话框，点击open 图标，加载四张素材图片中的一张 
5、保存并关闭对话框 
注意：如果你觉得这样的操作方法太慢，繁琐，你可以直接把图片拖入到画布中，和PS操作差不多，Construct2会自动为该图片创建Sprite对象。 

移动子弹和爆炸对象到画布外，这样游戏一开始，我们看不到这些对象。 
默认CT2会自动把我们的对象命名为Sprite,Sprite2,Sprite3,Sprite4，我们可以在他们各自的Properties bar属性面板里的Name属性里更改。依次更改Player,Monster,Bullet,Explosion（玩家，怪物，子弹，爆炸特效）。 

添加行为 
Behaviors类似于flash中的行为（动作），是预先封装的功能函数。例如，我们添加一个Platform行为给一个对象，添加Solid行为给地板，游戏运行时，该对象就可以象platformer游戏（例如：超级玛丽）中的角色一样跳来跳去。你也可以通过事件来达到同样的效果，但是这需要较长的时间，而且该预置的行为已经很好。 

Construct2具有以下行为： 

    Direction movement: 这个行为可以让你实现给角色添加方向移动（方向键）的功能。 

    Bullet movement:这个行为让对象朝着它当前的角度移动，比如，本例中玩家射出的子弹的移动行为，不要被这名字迷惑了，它不只适用于子弹，也可以应用于怪物等移动。在Contruct2里所有的移动行为都是通过添加速度向前行进。 

    Scroll to：这个行为可以让运行时画布随着对象移来移去（滚动）。这个行为很适合于角色。 
    
    Bound to layout：这个行为可以防止对象离开画布区域。这个行为对于角色来说也很重要。 
    
    Destroy outside layout:当对象离开画布区域时，就将其销毁。比如本例中的子弹，如果不销毁的话，虽然子弹离开画布区域了，但是依然暂用内存。所以我们需要及时销毁不再需要的对象。 
    
    Fade:这个行为可以给对象添加淡出效果，用于爆炸等特效的消失。 
    添加游戏功能 


通过上边的学习，我们已经学会了添加事件，教程到这，已经很长了，我们会发现教程看起来很啰嗦，太细，做起来一下子就完了，所以接下来我们稍微简化下。记住添加条件或动作的步骤如下： 

1、双击添加新事件，点击Add action链接添加一个动作。 

2、在对话框中双击要添加条件/动作的对象 

3、选取要添加的条件/动作 

4、如果有需要的话，输入参数 

让角色可以射击 
当玩家点击的时候，可以发射子弹。这可以通过Spawn an object动作来实现，该动作在同样的位置和角度（相对于角色）创建新的对象实例。子弹的Bullet movement属性将会使它向前飞出。 

最后一步 
教程接近尾声了，我们再添加一些功能并总结。 

添加如下事件： 

条件：System->Every X seconds->3 
//添加系统事件每3秒启动 

动作：system->Create object->Monster，layer 1，1400(for X)，random(1024)(for Y) 
//在图层1创建怪物实例，坐标可以自己指定，这里为画布最右边还过去点，已离开画布，因为我们画布的大小为1280，1024，Y坐标为随机数0-1024 。

  最后贴上几张制作出的游戏的“成果图”。
![这里写图片描述](https://img-blog.csdn.net/20171008205456581?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfNDAzMjgzMzQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](https://img-blog.csdn.net/20171008205638582?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfNDAzMjgzMzQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](https://img-blog.csdn.net/20171008205704599?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfNDAzMjgzMzQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)       

![这里写图片描述](https://img-blog.csdn.net/20171008205731555?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfNDAzMjgzMzQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)