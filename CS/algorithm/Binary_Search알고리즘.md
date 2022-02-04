# Q.  Binary search 알고리즘 작성하시오   (⭐⭐)

## 나의 답변

### binary search 알고리즘
- 검색 알고리즘이다.
- 중간 값을 검색하고, 그 기준으로 크면 오른쪽, 작으면 왼쪽으로 간다.
- O(logn)이 걸린다
- 정렬이 되있어야 한다. ( 오름 차순 )
- 분할 정복으로 진행된다.

### 분할 정복
**분할(Divide)**
- 리스트를 중간값을 기준으로 두개의 서브 리스트로 나눈다.

**정복(Conquer)**
- 검색할 숫자 < 중간값 이면, 앞 부분의 서브 리스트에서 검색할 숫자를 찾는다.
- 검색할 숫자 > 중간값 이면, 뒷 부분의 서브 리스트에서 검색할 숫자를 찾는다.
- 검색할 숫자 == 중간값 이면, 해당 값 혹은 true 리턴.

### 코드활용
```
int BSearch(int arr[], int target) {
    int low = 0;
    int high = arr.length - 1;
    int mid;

    while(low <= high) {
        mid = (low + high) / 2;

        if (arr[mid] == target)
            return mid;
        else if (arr[mid] > target)
            high = mid - 1;
        else
            low = mid + 1;
    }
    return -1;
}
```
