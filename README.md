# Compiler Construction

이 레포는 **컴파일러구성론**(Compiler Construction) 수업의 실습/정리 저장소입니다.  
프런트엔드(어휘·구문·의미) → IR → 백엔드(최적화·코드 생성)의 표준 파이프라인을 따라 주차별로 정리합니다.

## 교재 & 참고
- Andrew W. Appel, *Modern Compiler Implementation in C*, Cambridge Univ. Press.  
  (Part I가 각 컴파일러 단계별로 구성되어 있음)
- 강의 슬라이드(Prof. Hal Perkins, UW · 교수님 제공본)

## 진행 순서(요약)
1. Lexical Analysis → 2. Parsing → 3. Abstract Syntax → 4. Semantic Analysis  
5. Activation Records → 6. IR Translation → 7. Canonicalization/Basic Blocks  
8. Instruction Selection → 9. Control/Dataflow → 10. Register Allocation → 11. Code Emission
