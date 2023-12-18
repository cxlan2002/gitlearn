# learngit2019
#### 四级标题
内容内容`内容`内容内容内容
##### 五级标题
	内容内容`内容`内容内容内容
	内容内容内容`内容`内容
// 定义要倒计时的分钟数
const minutes = 48*60;

// 将分钟转换为毫秒
const totalMilliseconds = minutes * 60 * 1000;

// 获取当前时间戳
const startTime = Date.now();

// 定义 requestAnimationFrame 循环的函数
function updateTimer() {
  // 计算已经过去的时间
  const elapsedMilliseconds = Date.now() - startTime;

  // 计算剩余的时间
  const remainingMilliseconds = totalMilliseconds - elapsedMilliseconds;
    console.log('已经过去的时间'+elapsedMilliseconds,'剩余的时间'+remainingMilliseconds)

  // 如果剩余时间小于 0，则倒计时结束
  if (remainingMilliseconds <= 0) {
    // 停止 requestAnimationFrame 循环
    cancelAnimationFrame(animationFrameId);

    // 显示倒计时结束的消息
    console.log('倒计时结束');
  } else {
    // 更新倒计时显示
       // 获取毫秒
      const millisecond = remainingMilliseconds % 1000;
      // 获取秒数
      const second = Math.floor(remainingMilliseconds / 1000);
      // 获取分钟数
      const minute = Math.floor(second / 60);
      // 获取小时数
      const hour = Math.floor(minute / 60);
      // 获取天数
      const day = Math.floor(hour / 24);
      // 构造返回结果
      let showtime = `${day}天${hour % 24}时${minute % 60}分${second % 60}秒${millisecond}毫秒`;
      document.querySelectorAll('.hd')[0].innerHTML = showtime;
    console.log(showtime);

    // 继续 requestAnimationFrame 循环
    animationFrameId = requestAnimationFrame(updateTimer);
  }
}

// 启动 requestAnimationFrame 循环
let animationFrameId = requestAnimationFrame(updateTimer);
