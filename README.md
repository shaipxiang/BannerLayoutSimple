# BannerLayoutSimple

支持图片无限轮播的控件

##支持功能

- 支持网络本地加载数据

- 可自定义小圆点状态，左 中 右

- 可自定义title状态，左 中 右

- 可自定义提示栏状态，上 中 下

- 可自定义小圆点

- 可自定义是否自动轮播

- 支持List 、数组 两种数据格式

- 支持点击事件

- 支持设置轮播速度

- 支持是否显示小圆点，title,或者整个提示栏

- 支持加载时和加载失败时图片显示状态

- 支持选择暂停 恢复 轮播状态

##使用效果
![](http://i.imgur.com/UXFFMDx.gif)

##基础使用方法

>项目中引用 

		compile 'com.ydevelop:bannerlayout:0.0.1'

>如果是网络加载图片 记得添加

	<uses-permission android:name="android.permission.INTERNET" />

1.数组方式

        BannerLayout bannerLayout = (BannerLayout) findViewById(R.id.bannerLayout);
        int[] mImage = new int[]{R.drawable.banner1, R.drawable.banner2, R.drawable.banner3};
        String[] mTitle = new String[]{"bannerl", "banner2", "banner3"};
        bannerLayout
                .initImageArrayResources(mImage, mTitle)
                .initAdapter()
                .initRound(true, true, true)
                .start(true);

2.List集合

        BannerLayout bannerLayout = (BannerLayout) findViewById(R.id.bannerLayout);
        List<BannerModel> mDatas = new ArrayList<>();
        mDatas.add(new BannerModel("http://ww2.sinaimg.cn/bmiddle/0060lm7Tgw1f94c6kxwh0j30dw099ta3.jpg", "那个时候刚恋爱，这个时候放分手"));
        mDatas.add(new BannerModel("http://ww4.sinaimg.cn/bmiddle/0060lm7Tgw1f94c6qyhzgj30dw07t75g.jpg", "羞羞呢～"));
        mDatas.add(new BannerModel("http://ww1.sinaimg.cn/bmiddle/0060lm7Tgw1f94c6f7f26j30dw0ii76k.jpg", "腿不长 但细"));
        mDatas.add(new BannerModel("http://ww4.sinaimg.cn/bmiddle/0060lm7Tgw1f94c63dfjxj30dw0hjjtn.jpg", "深夜了"));
        bannerLayout
                .initImageListResources(mDatas)
                .initAdapter()
                .initRound()
                .start(true);	

3.点击事件，也可以自己单独写

		bannerLayout
                .initImageArrayResources(mImage, mTitle)
                .initAdapter()
                .initRound()
                .start(true)
                .setOnBannerClickListener(new BannerLayout.OnBannerClickListener() {
                    @Override
                    public void onBannerClick(int position) {

                    }
                });

4.提示栏及小圆点、title位置的改变

想要改变位置在initRound()方法中实现几种不同的状态，不需要的可以直接传null 有默认的参数

代码中提供了三个枚举

- BANNER_ROUND_CONTAINER_POSITION 	 提示栏在布局中的位置，TOP,BUTTOM,CENTERED三种可选 
- BANNER_ROUND_POSITION  	小圆点在提示栏的位置，LEFT,CENTERED,RIGHT三种可选 
- BANNER_TITLE_POSITION  	title在提示栏的位置，LEFT,CENTERED,RIGHT三种可选   


>最后调用start（）的时候可以决定是否开启自动轮播，不管在fragment还是activity里面，应该在合适的生命周期里选择暂停或者恢复轮播（如果开启了自动轮播），BannerLayout已经提供了方法，使用者直接调用就可以了，如果使用List数据，请使用BannerModel

## 自定义参数详解

属性名								|说明  						|属性值
---    								|---   						|---
delay_time   						|轮播时间					|默认2s
start_rotation   					|是否开启自动轮播				|true 开启，默认不开启	
view_pager_touch_mode   			|viewpager是否可以手动滑动	|true禁止滑动,false可以滑动，默认可以滑动
round_selector   					|小圆点状态选择器				|可参考自带的
round_container_background_switch   |是否显示提示控件的背景		|true 显示，默认不显示
round_left_margin   				|小圆点的marginLeft			|默认10	
round_right_margin   				|小圆点的marginRight			|默认10	
title_left_margin   				|title marginLeft			|默认10	
title_right_margin   				|title marginRight			|默认10	
round_width   						|小圆点width					|默认15
round_height   						|小圆点height				|默认15
round_container_background   		|BannerRound背景色			|默认半透明色
round_container_width   			|BannerRound宽度				|填充屏幕
round_container_height 				|BannerRound高度				|默认50
glide_error_image  					|glide加载错误占位符			|默认android自带图标
glide_place_image  					|glide加载中占位符			|默认android自带图标
banner_round_visible  				|是否显示小圆点				|默认显示
banner_title_visible  				|是否显示title				|默认不显示
banner_title_size   				|字体大小					|默认12
banner_title_color 					|字体颜色					|默认黄色

#最后
	
BannerLayout这个类里面的注释我感觉已经很详细了，如果上面的设置有不懂得可以看BannerLayout。
我一个人肯定测不出来所有bug，所以现在我也不知道哪里还有问题，基本的使用暂时没发现问题。
如果有人在使用的过程中出现未知或者莫名其妙的bug，欢迎提 [lssues](https://github.com/7449/BannerLayoutSimple/issues),
至于图片加载我直接是内置了Glide来加载图片。不管本地或者网络的图片都可以，但是要记得添加网络权限


License
--
    Copyright (C) 2016 yuezhaoyang7449@163.com

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.