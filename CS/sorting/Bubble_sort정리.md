# Q.  Bubble sort에 대해 정리하라 (⭐)

## 나의 답변

### Bubble sort
- 앞에서 부터 한개와 그 다음 것을 비교하면서 숫자가 작으면 왼쪽으로, 크면 오른쪽으로 보냄
- 위의 과정을 갯수만큼 반복함
- (n-1) + (n-2) ... + 2 + 1 = n(n-1)/2 로 비교횟수가 N제곱이 된다.
- 정렬하는데 O(n^2)이 걸림

```
void bubble_sort(int list[], int n){
  int i, j, temp;

  for(i=n-1; i>0; i--){
    // 0 ~ (i-1)까지 반복
    for(j=0; j<i; j++){
      // j번째와 j+1번째의 요소가 크기 순이 아니면 교환
      if(list[j]<list[j+1]){
        temp = list[j];
        list[j] = list[j+1];
        list[j+1] = temp;
      }
    }
  }
}
```
