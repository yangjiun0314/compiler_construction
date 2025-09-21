# 03 · Automata & Scanner Patterns

이번 주는 **RE → NFA → DFA** 흐름과 **스캐너 DFA 패턴**을 손으로 이해하는 주차다.  
핵심: (1) RE 규칙으로 NFA를 만들고, (2) 부분집합 구성으로 DFA를 얻어, (3) 스캐너는 DFA로 **Longest-Match**를 구현한다.

## Learning Objectives
- DFA vs NFA의 구조·동작을 설명할 수 있다.
- RE의 세 연산(연접, 선택, Kleene-*)에 대한 **NFA 구성 규칙**을 그릴 수 있다.
- **부분집합 구성(subset construction)**으로 NFA → DFA를 표로 전개할 수 있다.
- 스캐너 DFA 패턴(괄호/세미콜론, 단/다문자 연산자, INT, ID·키워드)을 말과 그림으로 설명할 수 있다.

## TL;DR 핵심 요약
- **FA 구성요소**: 유한 상태 집합, 초기 상태, 하나 이상 최종 상태, Σ(알파벳), 전이(문자 또는 ε)  
- **동작**: 입력을 왼→오로 읽으며 전이; 입력 소진 시 최종 상태면 accept  
- **DFA vs NFA**: DFA는 어떤 상황에서도 전이 선택이 **하나**; NFA는 **선택**이 허용(ε 포함)  
- **RE → NFA(핵심 규칙)**:
  - 원자: `a`는 a-라벨 1개 간선 / `ε`는 ε-전이만
  - 연접 `rs`: r의 accept에서 s의 start로 ε
  - 선택 `r|s`: 새 start에서 각각 r,s로 ε; r,s의 accept에서 새 accept로 ε
  - 반복 `r*`: r 주위에 새 start/accept 추가, 진입/유지/탈출 ε 구성
- **NFA → DFA**: **부분집합 구성**(ε-closure, move 집합을 상태로) → 필요 시 최소화
- **스캐너 DFA**: “마지막 accept 위치”를 기억 → 막히면 그 지점까지 토큰 확정(= Longest-Match)

## Scanner DFA 패턴(Hand-written)
- 단일 기호: `(`, `)`, `;` → 각각 단일 accept 상태
- 단/다문자 연산자: `!`/`!=`, `<`/`<=` → 분기 후 lookahead 처리(다문자 우선)
- 정수: `[0-9][0-9]*` 루프
- ID/키워드: `[A-Za-z_][A-Za-z0-9_]*` 수집 후 키워드 테이블로 분류 or DFA로 직접 인식

## Exercises (예제는 /examples)
1) `b(at | ag) | bu*g` 의 NFA 구성  
2) `10+1` 의 NFA를 그리고 DFA로 부분집합 구성  
3) `[01]*1` 의 NFA를 그리고 DFA로 부분집합 구성

## Review Checklist
- [ ] RE 세 연산의 NFA 구성 규칙을 빈 종이에 그릴 수 있다.
- [ ] ε-closure, move, dtran 표를 손으로 채울 수 있다.
- [ ] 다문자 연산자(`!=`, `<=`)가 단문자보다 우선 매치되는 이유를 말할 수 있다.
- [ ] ID vs 키워드를 DFA/룰 우선순위로 처리하는 전략을 말할 수 있다.
