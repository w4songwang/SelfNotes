
### AST抽象语法树
- [编程语言的实现，从AST（抽象语法树）开始](https://baijiahao.baidu.com/s?id=1626159656211187310&wfr=spider&for=pc)
- [AST抽象语法树——最基础的javascript重点知识，99%的人根本不了解](https://segmentfault.com/a/1190000016231512?utm_source=tag-newest)
- [the-super-tiny-compiler](https://github.com/jamiebuilds/the-super-tiny-compiler)



### html自动滚动
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>

        * {
            margin: 0;
            padding: 0;
        }

        #div_con {
            position: relative;
            width: 300px;
            height: 350px;
            margin: 20px;
            border: 2px solid #eee;
            overflow: hidden;
        }

        #div_msg {
            position: absolute;
            width: 280px;
            height: auto;
            margin: 0;
            padding: 10px;
            border: 0px solid red;
        }
    </style>
</head>
<body>

    <!--灰色边框容器div-->
    <div id='div_con'>

        <!--消息div-->
        <div id='div_msg'>

        </div>
    </div>


    <script src="//cdn.bootcss.com/jquery/2.2.2/jquery.js"></script>
    <script>var msg1 = '<h2>嫦娥四号中继星成功发射 将搭建地月“鹊桥”</h2> ' +
        '<img style="width:100%" src="http://img0.utuku.china.com/650x0/mili/20180521/444bb55a-dbd3-4b99-9aba-6e13974fcaa9.jpg" />' +
        '新华社西昌5月21日电（记者白国龙、余晓洁）21日5时28分，我国在西昌卫星发射中心用长征四号丙运载火箭，成功将探月工程嫦娥四号任务“鹊桥”号中继星发射升空。这是世界首颗运行于地月拉格朗日L2点（简称地月L2点）的通信卫星，将为2018年底择机实施的嫦娥四号月球背面软着陆探测任务提供地月间的中继通信。<br/>' +
        '长征四号丙运载火箭飞行25分钟后，星箭分离，将“鹊桥”直接送入近地点高度200公里，远地点高度40万公里的预定地月转移轨道，卫星太阳翼和中继通信天线相继展开正常。后续，“鹊桥”将经中途修正、近月制动和月球借力，进入月球至地月L2点的转移轨道，通过3次捕获控制和修正后，最终进入环绕地月L2点的使命轨道，地月L2点是卫星相对于地球和月球基本保持静止的一个空间点。<br/><br/> ';

    var msg2 = '<h2>辽宁号航母和056轻护同框组“最萌身高差” </h2> ' +
        '2018-05-21 13:32 <br/>' +
        '<img style="width:100%" src="https://t1.huanqiu.cn/5e798738c0d468b49b3534087f910a1e.jpg" />' +
        '【环球网军事综合报道】有照片显示中国海军辽宁号航母在航行时，在右舷前方有一艘056型轻型护卫舰航行的情景。辽宁号是目前中国海军现役最大的水面战舰，而056型则是中国一款轻型护卫舰，仅有1400吨，两艘军舰组成了“最萌身高差”。<br/>' +
        '在辽宁舰面前，056型护卫舰就是一个小不点<br/><br/> ';

    var msg = msg1 + msg2;

    //先赋值div
    $('#div_msg').html(msg);
    //获取div的高度
    var msg_height = $('#div_msg').height();

    //加2次，这样完全移动完的时候不至于出现空白
    $('#div_msg').html(msg + msg);

    var con_height = $('#div_con').height();

    var sub_height = con_height - msg_height;
    console.log('msg_height=' + msg_height + ', con_height=' + con_height + ",sub_height=" + sub_height);

    //当前顶部坐标
    var cur_top = 0;

    function scrollme() {
        cur_top--;

        //如果整个消息都已经上移完了，则重新赋值消息，及移动距离
        if (0 == cur_top + msg_height) {
            console.log('已经移完了,开始下一次')
            cur_top = 0;
        }

        $('#div_msg').css('top', cur_top + 'px');
    }

    setInterval("scrollme()", 20);</script>
</body>
</html>
``` 
