// Practice
// 1, 2, 3, 4 를 이용하여 세자리 자연수를 만드는 방법 (순서 X, 중복 x)의 각 결과를 출력하시오

public class Practice {
    void combination(int[] arr, boolean[] visited, int depth, int n, int r) {
        if (r == 0) { // return 조건
            for (int i = 0; i < n; i++) {
                if (visited[i]) { // true인 애들만 출력
                    System.out.print(arr[i] + " ");
                }
            }
            System.out.println();
            return;
        }

        if (depth == n) {
            return;
        } // 끝까지 다 돌아서 return

        visited[depth] = true;
        combination(arr, visited, depth + 1, n, r - 1); // 재귀 형태

        visited[depth] = false;
        combination(arr, visited, depth + 1, n, r);
    }
    
    public static void main(String[] args) {
//      Test code
        int[] arr = {1, 2, 3, 4};
        boolean[] visited = {false, false, false, false};

        Practice p = new Practice();
        p.combination(arr, visited, 0, 4, 3);
    }
}

/*
arr = 1 2 3 4
vi~ = 0 0 0 0
depth = 0
r = 3

arr = 1 2 3 4
vi~ = 1 0 0 0
depth = 1
r = 2

arr = 1 2 3 4
vi~ = 1 1 0 0
depth = 2
r = 1

arr = 1 2 3 4
vi~ = 1 1 1 0
depth = 3
r = 0

if (r==0)에 걸림 -> out : 1 2 3

depth = 2

arr = 1 2 3 4
vi~ = 1 1 0 0

depth = 3
r = 1
arr = 1 2 3 4
vi~ = 1 1 0 1

depth = 4
r = 0
arr = 1 2 3 4
vi~ = 1 1 0 1

out : 1 2 4
...

 */
