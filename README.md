- 👋 Hi, I’m @AMeyous
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
AMeyous/AMeyous is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import  *  as  Kalidokit  from  'kalidokit' 
import  '@mediapipe/holistic/holistic' ; 
导入 '@mediapipe/camera_utils/camera_utils' ；

让 整体 = 新的 整体（{ locateFile：（文件） =>  {
    返回 `https://cdn.jsdelivr.net/npm/@mediapipe/holistic@0.4.1633559476/ $ {文件} ` ; 
} } ）;

整体的。onResults （结果=> { 
    //使用预测结果的东西
    根据TFJS / Mediapipe模型版本//标名可以改变
    让 facelm  = 结果。faceLandmarks ;
    让 poselm  = 结果。poseLandmarks ;
    让 poselm3D  = 结果。EA ;
    让 rightHandlm  = 结果。rightHandLandmarks ;
    让 leftHandlm  = 结果。左手地标；

    让 faceRig  =  Kalidokit 。脸。解决( facelm , { runtime : 'mediapipe' , video : HTMLVideoElement } )
    让 poseRig  =  Kalidokit 。姿势。解决（poselm3d ，poselm ，{运行时：'mediapipe' ，视频：HTMLVideoElement } ）
    让 rightHandRig  =  Kalidokit 。手. 解决( rightHandlm , "Right" )
    让 leftHandRig  =  Kalidokit 。手。解决( leftHandlm , "Left" )

    } ; 
} ) ;

//使用Mediapipe的网络摄像头utils的发送视频到整体每一帧
const的 相机 = 新 相机（HTMLVideoElement ， { 
  onFrame：异步 （） =>  { 
    AWAIT 整体性。发送（{图像：HTMLVideoElement } ）; 
  } ，
  宽度：640 ，
  高度：480 
} ）; 
相机。开始( ) ;
