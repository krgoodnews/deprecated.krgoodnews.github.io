---
layout: post
title : Youtube Player 만들기
desc: iOS 앱에서 유투브 영상을 틀어보자.

---

서버에서 유투브 URL을 전달받으면 동영상에 재생해야한다.
 
당연히 `AVFoundation`을 사용하면 될 줄 알았다. 하지만 안됐다. 동영상 파일의 URL이 아니면 안된다고 한다.

라이브러리를 사용하고 싶지 않아서 [BodNuk의 튜토리얼](https://www.youtube.com/watch?v=rVcOY_qpMMg)도 보고 해봤다. 하지만 테두리쪽에서 뭔가 이상한게 있어서, 부족한 시간 때문에 어쩔 수 없이 라이브러리를 사용하게 된다.

----------------------------------------

#### 사용 라이브러리: [youtube ios player helper](https://github.com/youtube/youtube-ios-player-helper)
1. pod "youtube-ios-player-helper", "~> 0.1.4"
2. 스토리보드에 UIView 생성 후 YTPlayView로 클래스 변경, viewController와 연동
	* 혹은 코드로 UIView 생성
3. `youtubeView.load(withVideoId: "S8i9LpTWVts")` 하면 끝

* [각종 파라미터](https://developers.google.com/youtube/player_parameters)를 이용해서 뷰를 원하는대로 커스터마이징 할 수 있다.
	
		youtubeView.load(withVideoId: "S8i9LpTWVts", playerVars:
	          ["fs": 0,   // 동영상 최대화버튼 표시안함
	                "playsinline": 1,  // 동영상 재생시 별도 컨트롤러 생성하지 않음
	                "rel": 0,  // 동영상 종료후 관련 영상 표시하지 않음
	                "color": "white"
		//           "modestbranding": 1 // 유투브 로고를 숨긴다는데 안숨겨지는것같다.
		//           "showinfo": 0
				])