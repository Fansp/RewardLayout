# RewardLayout
仿斗鱼送礼物效果
> 关于我，欢迎关注  
  邮箱：437220638@qq.com
  如果对你有点帮助的话，点个star哦~
 
## Screenshots
![image](/screenshots/photo.gif)

## Statement
本项目旨在提供实现参考，交流学习
可自定义礼物item布局，动画，最大条数，每种礼物持续时间，定义好自己的BaseGiftBean及SendGiftBean可轻松实现自定义的效果，最大礼物数和礼物停留时间都可在xml上或者代码直接定义，具体接入请参考demo

## 快速预览
Activity
 ```java
    bean1 = new SendGiftBean(1,1,"林喵喵");// 构建发送礼物的bean包含礼物id，name和userid,username
    bean2 = new SendGiftBean(2,2,"马甲");
    bean3 = new SendGiftBean(3,3,"小梦梦");
    bean4 = new SendGiftBean(4,4,"大枫哥");
    bean5 = new SendGiftBean(4,1,"大枫哥");
    rewardLayout.setGiftItemRes(R.layout.gift_animation_item);//设置礼物item布局
    rewardLayout.setInitListener(new RewardLayout.GiftListener() {// 初始化，更新，载入动画，
    //以及数字动画的回调，可以自定义
        @Override
        public View onInit(View view, BaseGiftBean bean) {
            ...//参考 demo
            return view;
        }

        @Override
        public View onUpdate(View view, BaseGiftBean bean) {
            ...//参考 demo
            return view;
        }

        @Override
        public void addAnim(final View view) {
           ...//参考 demo
        }

        @Override
        public  AnimationSet outAnim() {
           ...//参考 demo
        }
    });
        
        @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.tvSendone:/*礼物1 林喵喵*/
                rewardLayout.showGift(bean1);
                break;
            case R.id.tvSendtwo:/*礼物2 马甲*/
                rewardLayout.showGift(bean2);
                break;
            case R.id.tvSendthree:/*礼物3 小梦梦*/
                rewardLayout.showGift(bean3);
                break;
            case R.id.tvSendfor:/*礼物4 枫哥*/
                rewardLayout.showGift(bean4);
                break;
            case R.id.tvSendanother:/*礼物1 枫哥*/
                rewardLayout.showGift(bean5);
                break;
        }
    }
```
XML
 ```java
<com.zhangyf.reward.view.RewardLayout
        android:id="@+id/llgiftcontent"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="100dp"
        android:animateLayoutChanges="true"
        app:max_gift="3"
        android:orientation="vertical" />
```
Config
 ```java
  GiftConfig.getInstance()
                .setGiftCount(4)
                .setGiftIds(new int[] {1,2,3,4})
                .setGiftNames(new String[] {"糖果","666","小香蕉","大鱼丸"})
                .setGiftRes(new int[] {R.mipmap.tg,R.mipmap.good,R.mipmap.banana,R.mipmap.yw})
                .setStayTimes(new long[] {2000,2500,2700,5200});
 ```
## Todo
v1.2 生成lib库,发布到jcenter
由于时间匆忙，界面，动画，数据的抽离，如果又发现任何Bug或者改进的意见欢迎提issue或者邮件#，#

 
## Fixed 
v1.0 已改进不同礼物消失机制，采用postHandler及removeCallbacks去更新和执行删除时机，可以通过config自定义每种礼物不同的持续时间，同时已优化不同人对同种礼物的区分
v1.1 修复快速送礼物重复问题

## Thanks
感谢许同学提供的切图
