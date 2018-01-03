# ZoomImageView
自定义的可放大缩小的ImageView<br>
想做到图片支持多点触控,并且能够自由的进行缩放和平移,需要了解几个知识点:<br>
### 1,Matrix<br>
数据结构:三维矩阵<br>
内部存储: new Float[9],内部就是一个一维数组,共九个元素,可以通过setValues(float[] values)进行初始化<br>
        每个元素代表的意思:<br>
        
        {  
        MSCALE_X, MSKEW_X, MTRANS_X,    
                MSKEW_Y, MSCALE_Y, MTRANS_Y,    
                MPERSP_0, MPERSP_1, MPERSP_2    
        };   
 操作:<br>
 如果你想要设置matrix的偏移量为200，100,你可以这么写<br>
 
    Matrix transMatrix = new Matrix();  
        float[] values = new float[] { 1.0, 0, 200, 0, 1.0, 100, 0, 0, 1.0 };  
        transMatrix.setValues(values);  
        
 Matrix提供了一些常用的API,上面代码达到的效果我们使用api可以这么写：
 
    Matrix transMatrix = new Matrix();  
        transMatrix.postTranslate(200, 100); 
        
 x轴方向缩放比例的获取<br>
 
    public final float getScale()  
    {  
        scaleMatrix.getValues(matrixValues);  
        return matrixValues[Matrix.MSCALE_X];  
    }  
    
### 2,GestureDetector<br>
这个能够捕获到长按,双击等事件

### 3,ScaleGestureDetector<br>
这个用来检测缩放的手势

### 4,这个项目的好多代码我是看的似懂非懂,完全是照着作者博客编写的代码

