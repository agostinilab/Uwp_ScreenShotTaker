# Uwp_ScreenShotTaker
Take a screen shot with a video element on the UI

In UWP app there isn't an easy way to take a screenshot. The only way to do this is with a function named RenderTargetBitmap which recreate the visual tree of UI components at a specific point to a bitmap image. This is working fine until your UI doesn't contain video elements (MediaElement which is playing video file). This problem is caused by design to prevent illegal grabbing of frames of protected (DRM) video files.

So if you try to use RenderTargetBitmap with a video file in the UI, the screenshot will result with a black rectangle in the position of MediaElement. To avoid this I came up with a dirty workaround: when I want to take a screenshot I will extract the frame from the video file, put it in a new Image Element, add the Image to the UI (setting a greater z-index), using RenderTargetBitmap to create the screenShot and then remove the Image element from the UI.

It's not clean but it works :)
