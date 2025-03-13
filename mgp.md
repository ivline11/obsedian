2주차
intell coffee lake
-> cpu 당 1 physical core -> 2 logical core -> 2 thread 
-> cpu 당 2 thread
hyperthreading / multithreading
6 cpu -> 12 thread 가 parallel 하게 처리 가능(동시에 병렬처리)

integrated cpu가 없는 자리에는 cache(fast memory)
cpu core - integrated GPU(X) 대신에 cache 가 있고 - 멀리 DRAM
Memory의 size와 bandwidth를 늘리기 위해 integrated gpu 자리에 cache를 크게 놔서 cpu와 가까운 자리에 memory를 놓는다.? 뭔소리지.. (xeon의 방식)

멀티쓰레딩 5376 fp32 unit - 84 major processing block
5376이 number of core라고 ? optimal number of thread는? 코어수와 같이 5000개 정도
코어수보다 쓰레드 수가 많아야 됨. (이유는 하드웨어 어쩌고)
코어수보다 4배는 많아야함. (그 이유를 배울것이다. 중간고사 이후에)

병렬처리(sum reduce)
병렬처리로 더하면 당연히 network 지연이 줄어든다.






