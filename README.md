# kline(尽量避免改动源码,方便修复bug重新依赖)
 ****************************************************
 * 有问题可以加群反馈,优化功能会同步到群                  
 * QQ群: __163565953__                                  
 * 功能持续优化,好用容易接入的K线                       
 ****************************************************
## 效果图
复用历史数据会导致K线看起来有点乱,数据问题

<img src="https://github.com/icechao/KlineChart/blob/master/7i7by-qncwl.gif" width="300" hegiht="500" align=center />


## 使用步骤: 

  1. <b>继承KlineEntry实现Bean类,复写对应方法返回 高 开 低 收 量 时间</b>
  
            public class KChartBean extends KLineEntity {
            
                  @Override
                  public Long getDate() {
                      try {
                          return new SimpleDateFormat("yyy/MM/dd").parse(date).getTime();
                      } catch (ParseException e) {
                          e.printStackTrace();
                          return 0L;
                      }
                  }

                  @Override
                  public float getOpenPrice() {
                      return open;
                  }

                  @Override
                  public float getHighPrice() {
                      return high;
                  }

                  @Override
                  public float getLowPrice() {
                      return low;
                  }

                  @Override
                  public float getClosePrice() {
                      return close;
                  }

                  @Override
                  public float getVolume() {
                      return volume;
                  }
                  ......
            }
          
  2. <b>在布局中直接使用</b>
  
            <com.icechao.klinelib.view.KLineChartView
              android:id="@+id/kLineChartView"
              android:layout_width="match_parent"
              android:layout_height="580dp"
              android:background="@color/color_081734" />
             
          支持自定义属性
              自定义属性查看:
             
        [属性列表](https://github.com/icechao/KlineChart/blob/master/klinelib/src/main/res/values/attrs.xml)
       | 名称 | 值 | 属性 | 默认 | 
       | ------ | ------ | ------ | ------ |  
       | maiLengendMarginTop  | dimension | 主视图Lengend上边距 | 10 |
       | paddingBottom  | dimension | chart上部内容边距 | 30,第一个网格的位置 |
       | paddingTop  | dimension | 主视图Lengend上边距 | 15底部显示X轴label空间 |
       | chartLogo  | resource | 主视图logo | |
       | candleRight_padding  | dimension | 主视图与右侧内边距 | |
       | increaseColor  | color | 涨颜色| |
       | backgroundColor   | color | 背景色  | |
       | decreaseColor  | color | 跌颜色| |
       | textSize  | dimension | 文字大小| |
       | textColor  | color | 文字颜色| |
       | lineWidth  | dimension | 指标线线宽 | |
       | kline_itemWidth  | dimension | 蜡烛图加外围空隙宽| |
       | candleWidth  | dimension | 蜡烛图柱宽 | |
       | candleLineWidth  | dimension | K线空心时宽度 | |
       | priceLineWidth  | dimension | 价格线宽 | 1dp |
       | priceLineColor  | color | 价格线颜色 | |
       | priceLineRightColor  | color | 价格只显示在右侧时颜色 | |
       | priceLineBackgroundColor  | color | 价格线横框背景色 | #CFD3A9 |
       | priceLineBoxMarginRight  | dimension | 价格框右边距 | 120 |
       | priceLineBoxShapeWidth  | dimension | 价格线框内三角形占宽| 10 |
       | priceLineBoxShapeHeight  | dimension | 价格线框内三角形占高| 20 |
       | priceLineBoxHeight  | dimension | 价格线上的框高度| 40 |
       | priceLineBox_padding  | dimension | 价格线上的框的内边距| 20 |
       | priceLineBoxShapeTextMargin  | dimension | 价格框文字与图形距离| 10 |
       | priceLineBoxBorderWidth  | dimension | 价格线框边框宽度| 1 |
       | priceLineBoxBorderColor  | dimension | 价格线框边框颜色| |
       | backgroundFillTopColor  | color |背景渐变上部颜色 | |
       | backgroundFillBottomColor  | color |背景渐变下部颜色 | |
       | backgroundAlpha  | integer | 背景色透明度| |
       | backgroundFillAlpha  | integer | 背景色填充透明度 | |
       | yLabelMarginRight  | dimension | y轴上label与右侧边距 |10 |
       | timeLineColor   | color| 分时线颜色| |
       | timeLineFillTopColor  | color | 分时线填充渐变上部颜色 | |
       | timeLineFillBottomColor  | color |背景色渐变下部颜色 | |
       | timeLine_end_pointColor  | color | 分时线尾颜色 | |
       | timeLine_endMultiply  | int | 分时线尾圆变化最大倍数 | |
       | timeLine_endRadiu  | dimension | 分时线尾圆半径 | |
       | candleSolid  | boolean | K线是否空心| false |
       | gridLineWidth  | dimension | 网格线宽| |
       | gridLineColor  | color | 网格颜色 | |
       | select_xLineWidth  | dimension | 十字线X轴线宽| |
       | selectLabelBoderWidth  | dimension | 选中坐标边框线宽| 2 |
       | selectLabelBoderColor  | color | 选中坐标边框颜色| |
       | select_yLineWidth  | dimension | 十字线Y轴线宽| |
       | select_xLineColor  | color |选择线X线颜色 | |
       | select_yLineColor  | color |  选择线Y线颜色| |
       | select_yColor  | color | 选择线Y渐变色,Y线最好半透明透明| |
       | selectCrossBigColor  | color | 选择线相交点圆颜色| |
       | selectCross_pointColor  | color |选择线相交点颜色 | |
       | selectCross_pointRadiu  | color |选择线相交点小圆半径 | |
       | select_priceBoxBackgroundColor  | color | 先中价格框背景色 | |
       | selectBackgroundColor  | color | 选择框背景色 | |
       | select_priceBoxHorizental_padding  | dimension | 选择后价格框的横向padding,三角形的高为横+纵padding | 4dp |
       | select_priceBox_vertical_padding  | dimension | 选择后价格框的纵向向padding,三角形的高为横+纵padding | 2dp |
       | select_infoBoxMargin  | dimension | 选中弹出框的margin | |
       | select_infoBox_padding  | dimension | 选中行弹出行情行间距,上下为此值*2 | |
       | select_infoBoxTextColor  | dimension | 选中行弹出行情的文字颜色 | Color.WHITE |
       | select_infoBoxBorderColor  | dimension | 选中行弹出行情的边框颜色 | Color.WHITE |
       | select_infoBoxBackgroundColor  | dimension | 选中行弹出行情的背景颜色 | Color.DKGRAY |
       | selectTextSize  | dimension | 选择框文字大小 | |
       | macd_increaseColor  | color | macd标准线上柱颜色| |
       | macd_decreaseColor  | color | macd标准线下柱颜色 | |
       | macdWidth  | dimension | macd柱状图宽度 | |
       | difColor  | color | dif线颜色 | |
       | deaColor  | color | dea线颜色 | |
       | macdColor  | color | macd线颜色 | |
       | kColor  | color | k线的颜色 | |
       | dColor  | color | d线的颜色 | |
       | jColor  | color | j线的颜色 | |
       | rsi1Color  | color | 第1根rsi线的颜色 | |
       | rsi2Color  | color |第2根rsi线的颜色 | 暂无 |
       | ris3Color  | color | 第3根rsi线的颜色 | 暂无 |
       | upColor  | color | up线颜色 | |
       | mbColor  | color | mb线颜色 | |
       | dnColor  | color | dn线颜色 | |
       | wr1Color  | color | 第1根wr线的颜色| |
       | wr2Color  | color | 第2根wr线的颜色| 暂无 |
       | wr3Color  | color | 第3根wr线的颜色| 暂无 |
       | ma1Color  | color | 第1根ma线的颜色 | |
       | ma2Color  | color | 第2根ma线的颜色 | |
       | ma3Color  | color | 第3根ma线的颜色 | |
       | volLengendColor   | color| 成交量图例颜色 | |
       | volLengendMarginTop  | dimension | 成交量图例距离成交量顶部距离 | 10 |

              
  3. <b>初始化k线</b>
  
              private void initKline() {
                     //设置K线的数据适配器
                     chartView.setAdapter(new KLineChartAdapter());
                     //设置X轴时间格式化对象,根据不同波段可以重新设置
                     chartView.setDateTimeFormatter(new DateFormatter());
                     //背景网络列
                     chartView.setGridColumns(5);
                     //背景网络行
                     chartView.setGridRows(5);
                     //设置Y轴值格式化对象,默认保留两位小数
                     chartView.setValueFormatter(new ValueFormatter() {
                         @Override
                         public String format(float value) {
                             return String.format("%.2f", value);
                         }
                     });
                     //设置交易量格式化对象,默认保留两位小数
                     chartView.getVolDraw().setValueFormatter(new ValueFormatter() {
                         @Override
                         public String format(float value) {
                             return String.format("%.2f", value);
                         }
                     });
                     //设置K线左侧滑动的超出距离
                     chartView.setOverScrollRange(getWindowManager().getDefaultDisplay().getWidth() / 5);
                     //显示loading
                     chartView.showLoading();
                 }
                 
         
  4.<b>使用KLineChartAdapter设置数据</b>
  
           如果没有将数据适配器保存可以通过ChartView的getAdapter方法获取
           chartView.getAdapter()
  
           填充或重新填充数据
           resetData(List<KlineEntry>);
           
           尾部追加数据 
           addLast(KlineEntry);
           
           修改某个数据 
           changeItem(KlineEntry);
           
           如果有需要在前面追加多个数据可以继承KLineChartAdapter自定义方法参考addLast方法

# 查看全部API点击[这里KLineChartView](https://github.com/icechao/KlineChart/blob/master/klinelib/src/main/java/com/icechao/klinelib/view/KLineChartView.java)或加QQ群咨询

# 部分API  ________  kLineChartView为KLineChartView对象
     
  ### Loadding展示

       kLineChartView.justShowLoading() ;
       
            只显示loading不会显示后面的K线,K线部队只显示背景
            
       kLineChartView.showLoading();
       
            显示loading的同时显示K线

  ### 主图MA/BOLL切换
        
        kLineChartView.changeMainDrawType(Status.MainStatus.MA);
            参数    
            Status.MainStatus.MA, : 显示ma  默认值
            Status.MainStatus.BOLL: 显示boll
            Status.MainStatus.NONE: 只显示CandleLine

  ### 子图指标图切换

        kLineChartView.setChildDraw(Status.ChildStatus.MACD);
            参数
            Status.ChildStatus.NONE : //不显示子图  默认值
            Status.ChildStatus.MACD : macd
            Status.ChildStatus. KDJ  : kdj
            Status.ChildStatus.RSI  : rsi
            Status.ChildStatus.WR   : wr

  ### 设置是适应X左右边轴坐标的位置

        kLineChartView.setBetterX(boolean betterX);
            参数
            true : X轴最左边和最右边label会向中间缩进显示保证label全部显示在屏幕内  默认值  
            false: 显示为X轴最左边和最右边label会以与对方的坐标点中间对齐的方式显示 
           
  ### K线与分时线切换

        chartView.setKlineState(Status.KlineStatus klineStatus);
            参数
            Status.KlineStatus.K_LINE    : 显示K线
            Status.KlineStatus.TIME_LINE : 显示为分时线
           
  ### 十字线跟随手指

        kLineChartView.setCrossFollowTouch(boolean crossFollowTouch) ;
            参数
            true : 跟随手指
            false: 显示为收盘价  默认值
           
  ### 动画加载加载数据时(默认是左到右的加载动画 可以加载数据前设置不使用动画)
        
        kLineChartView.setAnimLoadData(boolean withAnim);
            参数
            true : 执行加载数据动画  默认值
            false: 不执行加载数据动画
   
  ### K线右侧内边距
  
        kLineChartView.setKlineRightPadding(float klineRightPadding);
            参数
            float : 内边距
  
  ### 设置十字线显示模式
  
        kLineChartView.setSelectedTouchModle(Status.ShowCrossModle showCrossModle);
            参数 
            Status.ShowCrossModle.SELECT_TOUCHE : 点击显示
            Status.ShowCrossModle.SELECT_PRESS  : 长按显示
            Status.ShowCrossModle.SELECT_BOTH   : 点击长按混合
            
  ### 添加logo
  
        kLineChartView.setLogoBigmap(Bitmap bitmap);
            参数
            Bitmap : 图片Bitmap 可以设置好大后传入
        
        kLineChartView.setLogoResouce(int bitmapRes);
            参数
            bitmapRes : 资源id 原大小显示
            
  ### logo透明度设置
        
        kLineChartView.setLogoAlpha(int alpha);
            参数
            alpha : 0-255 logo画笔透明度
            
  ### logo位置是指
        
        kLineChartView.setLogoLeftTop(float left, float top);
            参数
            left : logo的左侧坐标,相对KlineChartView
            top  : logo的顶部坐标,相对KlineChartView
            
  ### K线滑动监听
        
        kLineChartView.setSlidListener(SlidListener slidListener);
            参数
            slidListener : SlidListener对象 监听滑动到最左和最右
            
  ### K线重置显示位置
        
         kLineChartView.setResetTranslate();
        
  ### K线右侧可左滑的空白距离
        
         kLineChartView.setOverScrollRange(float overScrollRange);
         参数
         overScrollRange : 滑动距离

            
       
### 功能及优化

  - 重写分时线绘制
  - 重写十字线绘制
  - 重写选中的绘制
  - 重写网格的绘制
  - 重写背景网格绘制
  - 重写Y轴label的绘制
  - 重写十字线纵线的绘制
  - 重写CandleLine绘制
  - 重写成交量柱状图的绘制
  - 重写数据计算
  - 重写滑动计算
  - 重写放大计算
  - 重写选中框的计算
  - 重写指标线的算法
  - 重写当前页面K线数目的计算
  - 添加深度图
  - 添加设置logo
  - 添加k线与右侧间距
  - 添加十字线选中模式
  - 添加当前价格的时间线
  - 添加分时线尾呼吸灯效果
  - 添加追加尾部数据的方法
  - 添加时间和值的动态格式化
  - 添加K线数据变化时动画效果
  - 添加加载数据的动画执行开关
  - 添加最新价格和屏幕右侧指示线
  - 添加十字线模式开关(选中Y值跟随手指或指向最新价)
  - 添加LoadingView设置(可以自定义View并自定义动画)
  - 添加X轴左右坐标显示模式开关(相对坐标点居中,屏幕内  默认屏幕内显示)
  - 删除加载更多逻辑(重置设置数据不需要加载更多)

  



