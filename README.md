# Future_Work
用于以后找工作相关事宜
### 并查集模板

```
class UnionFind{
    public:
        vector<int>father;
        UnionFind(int num){
            for(int i = 0; i < num ; i++)
                father.push_back(i);//箭头指向自己
        }
        int Find(int n){//寻找集合中的老大
            while(n != father[n]){
                father[n] = father[father[n]];
                n = father[n];
            }
            return n;
        }
        void Union(int a ,int b){//结合起来，形成集合
            int fa = Find(a);
            int fb = Find(b);
            father[fa] = fb;
        }
};
```


