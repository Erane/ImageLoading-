# ImageLoading
图片预加载

使用方法

```JavaScript

        ImageLoading(
                /*
                * 第一个参数 是需要预加载的图片数组 (如果不需要请传一个空数组[]当参数)
                * 第二个参数 是需要预加载的音频数组 (如果不需要请传一个空数组[]当参数)
                * 第三个参数 是回调函数
                *
                * */
                [
                    'img/1.jpg',
                    'img/2.jpeg',
                    'img/3.jpg',
                    'img/4.jpg'
                ],
                [
                    {
                        'src' : 'audio/m.mp3',
                        // 下面是可匹配参数 如果不写取下面的默认值
                        '_type' : 'audio/mpeg',
                        '_preload' : 'auto',
                        '_loop' : true,
                        'cb':function(){} // 回调函数
                    }
                ],
                {
                    loading : function(count,total){
                        // 加载中
                        /*
                         * count : 已加载完成的图片/音频数量
                         * total : 音频/图片总数
                         * */
                        console.log(Math.floor((count/total) * 100));
                    },
                    complete : function(time,audios){
                        // 加载完毕
                        /*
                         * time :   加载图片/音频总耗时 毫秒单位
                         * audios : 加载完成音频数组 具体调用方法如 audios[0].obj
                         * */
                        console.log(audios[0]);
                        function playAudio(obj){
                            if(window.HTMLAudioElement){
                                if(obj.paused){
                                    obj.play();
                                }else{
                                    obj.pause();
                                }
                            }
                        }
                        playAudio(audios[0].obj);
                    }
                }
        )

```
