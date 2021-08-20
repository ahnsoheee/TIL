## Cache (캐시)

- 데이터를 미리 복사해 놓는 임시 저장 장소
- 캐시에 데이터를 미리 복사해 놓으면 계산이나 접근 시간없이 더 빠른 속도로 데이터에 접근할 수 있다.

1. Cache miss
- 참조하려는 데이터가 캐시에 없는 경우
-> 캐시 교체 정책에 다라 기존 캐시를 교체한다.

2. Cache hit
- 참조하려는 데이터가 캐시에 존재하는 경우

3. 페이지 교체 알고리즘
- LRU(Least-Recently-Used) : 가장 오랫동안 사용되지 않은 데이터가 교체된다.
    [예제](https://github.com/ahnsoheee/Algorithm/blob/master/Programmers/2018_KAKAO_BLIND_RECREUITMENT/%5B1%EC%B0%A8%5D%20%EC%BA%90%EC%8B%9C.py)
- LFU(Least-Frequenly-Used) : 참조 횟수가 가장 적은 데이터가 교체된다.