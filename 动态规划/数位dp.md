
## 数位DP统计数字基本模版
```cpp
ll dfs(int pos, int cnt, bool limit, bool lead) { //dfs函数：统计从当前状态开始，目标数字共出现多少次
    if (pos == num.size()) return cnt; // 边界条件：处理完所有位，返回累计的个数cnt
    if (dp[pos][cnt][limit][lead] != -1) // 记忆化：如果当前状态已经计算过，直接返回
        return dp[pos][cnt][limit][lead];
    ll ans = 0; 
    int up = limit ? num[pos] : 9; // 确定当前位可以取的最大值:如果limit=1，则不能超过原数的当前位；否则可以取0-9
    for (int i = 0; i <= up; i++) { // 枚举当前位的所有可能取值
        bool nlimit = limit && (i == up); // 更新limit状态：只有之前limit为1，且当前取的i达到了上限up时，新的limit才为1
        bool nlead = lead && (i == 0);// 更新lead状态：只有之前是前导零，且当前取0时，才继续保持前导零
        int add = (!nlead && i == target) ? 1 : 0; // 判断当前位是否贡献一个目标数字,条件为不是前导零且等于target
        // 递归处理下一位
        // cnt+add: 累计目标数字的个数
        // nlim: 新的限制状态
        // nlead: 新的前导零状态
        ans += dfs(pos+1, cnt+add, nlimit, nlead);
    }
    return dp[pos][cnt][limit][lead] = ans;    // 记忆化存储并返回
}
ll solve(ll n, int d) { // solve函数：统计[1, n]中数字d出现的次数
    if (n < 1) return 0;
    num.clear(); // 清空num数组
    while (n) { // 将n的每一位数字提取到num中（从低位到高位）
        num.push_back(n % 10);  // 取个位
        n /= 10;                // 去掉个位
    }
    reverse(num.begin(), num.end()); // 反转：使得num[0]是最高位，num[n-1]是最低位
    target = d;
    memset(dp, -1, sizeof(dp)); // 重置记忆化数组为-1（表示未计算）
    return dfs(0, 0, 1, 1);
}
```
