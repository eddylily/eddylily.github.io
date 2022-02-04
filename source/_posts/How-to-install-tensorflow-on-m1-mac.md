---
title: M1 Mac에 TensorFlow 설치하기
date: 2022-01-21 22:15:48
tags: AI
---
</br>

뜬금없지만 자랑부터 하자면, 필자는 최근에 M1 Pro 칩셋이 탑재된 신형 맥북 프로를 선물받았다. (와!) 이전에 쓰던 맥북 에어와는 차원이 다른 빠릿함이 낯설게만 느껴졌다. 가히 최고의 성능을 자랑하는 맥북 프로이지만, 아직 문제점이 몇 가지 있다. 그 중 하나는 바로 기존의 x86 아키텍처에서 구동되던 프로그램들의 상당수가 Apple Sillicon(애플 실리콘, 최신 맥북에 탑재되는 애플이 자체 개발한 칩셋)에 최적화되어 있지 않다는 것이다.
<!-- more -->

</br>
TensorFlow를 다뤄본 적 없었던 필자는 우선 Anaconda-Navigator를 이용하여 가상 환경을 구축한 다음, TensorFlow를 설치하고자 했었다. 그러나 몇 번의 삽질과 구글링을 하던 와중에 Anaconda-Navigator가 애플 실리콘에서 제대로 구동되지 않는다는 정보를 알게 되었다. (아뿔싸!) 대신, 무려 애플 공식 개발자 사이트에서 애플 실리콘이 탑재된 Mac에 TensorFlow를 설치하는 방법을 친절하게 설명해 주고 있다는 사실 또한 알게 되었다. [(여기를 누르면 볼 수 있다)](https://developer.apple.com/metal/tensorflow-plugin/)

</br>

위의 링크로 들어가서 'arm64: Apple Sillicon' 이라는 제목 아래에 있는 과정들을 전부 따라하면 된다. 해당 포스팅에도 설명을 해 두겠다. 

</br>

우선 [여기에서](https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh) 애플 실리콘 전용 Conda env를 다운로드받은 다음, 아래의 명령어를 차례대로 터미널에 입력한다. 이는 애플 실리콘이 탑재된 Mac에서도 Conda 개발 환경을 구축할 수 있도록 해 주는 'Miniforge3'라는 툴을 설치하는 과정이다. 
</br>
    $ chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
    $ sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
    $ source ~/miniforge3/bin/activate
</br>
설치가 완료되었으면, 이번에는 아래 명령어를 입력하여 TensorFlow에 필요한 속성 파일들을 설치해준다.
</br>
    $ conda install -c apple tensorflow-deps
</br>
이제 거의 다 끝났다. 남은 것은 아래의 두 명령어를 터미널에 입력해주는 것뿐이다.
</br>
    $ python -m pip install tensorflow-macos
    $ python -m pip install tensorflow-metal
</br>
이렇게 해서 애플 실리콘이 탑재된 Mac에서 TensorFlow를 사용할 수 있게 되었다. Conda를 이용해 따로 가상의 개발 환경을 구축한 다음 Jupyter Notebook을 통해 사용할 수도 있는데, 이는 다음 포스팅에서 다루어보도록 하겠다. 
