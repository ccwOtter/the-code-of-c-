#ST表
```cpp
for (int i = 1; i <= n; i++) {
        st[i][0] = a[i];
    }
    logtable[1] = 0;
    for (int i = 2; i <= n; i++) {
        logtable[i] = logtable[i / 2] + 1;
    }
    for (int j = 1; j <= logtable[n]; j++) {
        for (int i = 1; i + (1 << j) - 1 <= n; i++) {
            st[i][j] = max(st[i][j-1], st[i + (1 << (j-1))][j-1]);
        }
    }
    while (m--) {
        int k = logtable[r - l + 1];
        int ans = max(st[l][k], st[r - (1 << k) + 1][k]);
        cout << ans << '\n';
    }
```
