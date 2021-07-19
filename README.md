# Speech_MFCC_GFCC_Python
求取语音的MFCC参数和GFCC参数，可用于语音信号特征提取,下载完成后解压scikits.zip文件夹到当前路径下即可使用

# 提取MFCC特征--运行mfcc_extractor.py

~~~python
 sr, wav_data = wavfile.read(u"clean.wav")
 #分别代表 （语音文件，采样率，帧长，帧移，mel,dct,加窗）
 mfcc, spect = mfcc_extractor(wav_data[:32000,], sr, sr//1000*20, sr//1000*10, 52, 26, 'hanning', True)
 pyplot.imshow(mfcc)
 pyplot.show()
~~~
# 提取GFCC特征--运行 gfcc_extractor.py

~~~python

 #读取语音文件
 sr, wav_data = wavfile.read(u"./data/clean.wav")
 # xx, sr, win_len, shift_len, channel_number, win_type
 # cochleagram_extractor内数字分别代表：帧长，帧移，DCT参数设置
 cochlea = cochleagram_extractor(wav_data, sr, 1024, 512, 32, 'hanning')
 # cochlea 是DCT之前的参数
 plt.matshow(cochlea)
 plt.show()
 gfcc = gfcc_extractor(cochlea, 32, 16)
~~~
