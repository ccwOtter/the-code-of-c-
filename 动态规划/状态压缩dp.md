```cpp
for(int i=1;i<=m;i++){
		for(int j=1;j<=n;j++){
			int k;
			cin>>k;
			mp[i]<<=1;
			mp[i]+=k;
		}
	}
	dp[0][0]=1;//不养植
	for(int i=1;i<=m;i++){//遍历每一行
		for(int j=0;j<(1<<n);j++){//遍历当前行的所有状态
			if((j&mp[i])!=j || (j<<1&j)) continue;//判断土地是否肥沃和左右是否相邻
			for(int k=0;k<(1<<n);k++){ //遍历上一行的所有状态
				if(!(j&k)){//判断上下不相邻
					dp[i][j]=(dp[i][j]+dp[i-1][k])%MOD; //状态转移
				}	
			}
		}
	}
	//统计结果：第m行所有状态的和 
	int ans=0;
	for(int i=0;i<(1<<n);i++)
		ans=(ans+dp[m][i])%MOD;
	cout<<ans<<endl;
```
