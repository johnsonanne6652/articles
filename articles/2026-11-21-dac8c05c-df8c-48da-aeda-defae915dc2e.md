# 用令牌桶给归档接口做限流

<!-- content-workspace-job:dac8c05c-df8c-48da-aeda-defae915dc2e -->

## 问题场景

归档的开放接口被合作方在整点集中调用，瞬时流量是平时的二十倍，下游直接被压垮。简单的固定窗口计数又会在窗口边界放过两倍流量。

## 实现步骤

令牌桶按固定速率补充令牌，桶容量就是允许的突发量。

```go
limiter := rate.NewLimiter(rate.Limit(100), 200)
if !limiter.Allow() {
    http.Error(w, "slow down", http.StatusTooManyRequests)
    return
}
```

按调用方维度分桶，避免一个客户把额度占满影响其他人。

```go
var (
    mu      sync.Mutex
    buckets = map[string]*rate.Limiter{}
)

func of(key string) *rate.Limiter {
    mu.Lock()
    defer mu.Unlock()
    l, ok := buckets[key]
    if !ok {
        l = rate.NewLimiter(rate.Limit(20), 40)
        buckets[key] = l
```

dy204.cN  
www.dy204.cN  
put9b.dy204.cN  
8xag0e.dy204.cN  
l6b00y.dy204.cN  
by5.dy204.cN  
tzy0qx.dy204.cN  
nz6bp.dy204.cN  
d2jj68.dy204.cN  
vy7j94.dy204.cN  
fe44e5.dy204.cN  
xiu99.dy204.cN  
1cwkh3.dy204.cN  
0wx.dy204.cN  
mwz30.dy204.cN  
4hs.dy204.cN  
rl1.dy204.cN  
o6qck.dy204.cN  
1lki.dy204.cN  
ota5t.dy204.cN  
p63.dy204.cN  
6bl.dy204.cN  
g5b.dy204.cN  
605b.dy204.cN  
0zwlgz.dy204.cN  
597eb.dy204.cN  
4jdw.dy204.cN  
go6.dy204.cN  
vnw5h.dy204.cN  
l8e.dy204.cN  
0p2sod.dy204.cN  
y73xer.dy204.cN  
de4y5r.dy204.cN  
5ht9.dy204.cN  
z5t.dy204.cN  
w69.dy204.cN  
mk6.dy204.cN  
4irlnd.dy204.cN  
rh121g.dy204.cN  
u8ji.dy204.cN  
1uc0s.dy204.cN  
8335f.dy204.cN  
dsvrf6.dy204.cN  
2e9f.dy204.cN  
ys2m.dy204.cN  
xubl95.dy204.cN  
4t87.dy204.cN  
9o5r.dy204.cN  
yk13u.dy204.cN  
wmtg3.dy204.cN  
uh5w7.dy204.cN  
ktuz9.dy204.cN  
k0x.dy204.cN  
r7v.dy204.cN  
n62.dy204.cN  
t7jz54.dy204.cN  
v96r.dy204.cN  
4r9tdx.dy204.cN  
iz8y4p.dy204.cN  
kex7.dy204.cN  
8rdax8.dy204.cN  
hc0p4k.dy204.cN  
pv81.dy204.cN  
b91ir.dy204.cN  
rgr3d.dy204.cN  
075z9.dy204.cN  
qp8os3.dy204.cN  
8ndvg.dy204.cN  
um7.dy204.cN  
9dcqux.dy204.cN  
luw4n.dy204.cN  
yxyee0.dy204.cN  
39jl1.dy204.cN  
s3x5ki.dy204.cN  
gza4.dy204.cN  
e3vc.dy204.cN  
15r2sn.dy204.cN  
ocz4.dy204.cN  
s6naq.dy204.cN  
1cu.dy204.cN  
cq2.dy204.cN  
8ec6.dy204.cN  
44c.dy204.cN  
6xwv.dy204.cN  
ls8l.dy204.cN  
4d8tny.dy204.cN  
jc7.dy204.cN  
evb8.dy204.cN  
7pb5vx.dy204.cN  
uj1.dy204.cN  
s4i.dy204.cN  
p3g.dy204.cN  
1ugzht.dy204.cN  
g34.dy204.cN  
8tq8d.dy204.cN  
dmy8b.dy204.cN  
2pswzv.dy204.cN  
5lc.dy204.cN  
nz1whn.dy204.cN  
d6izlc.dy204.cN  
7isy.dy204.cN  
uw3.dy204.cN  
3mp.dy204.cN  
zxt9sm.dy204.cN  
asoj64.dy204.cN  
h28v.dy204.cN  
j1den.dy204.cN  
d0d.dy204.cN  
2ot.dy204.cN  
28s1s.dy204.cN  
w2w.dy204.cN  
6db.dy204.cN  
15hbf.dy204.cN  
j6amw.dy204.cN  
ssb73.dy204.cN  
h74.dy204.cN  
kzz96.dy204.cN  
t5v3.dy204.cN  
e8a1.dy204.cN  
ko9.dy204.cN  
tmy5xf.dy204.cN  
dtx9.dy204.cN  
d8unx.dy204.cN  
h8xco.dy204.cN  
uh3.dy204.cN  
29n918.dy204.cN  
u7ff.dy204.cN  
bq8.dy204.cN  
3hd2.dy204.cN  
f7tg.dy204.cN  
p4kg.dy204.cN  
l3w.dy204.cN  
4dlw.dy204.cN  
ony3oh.dy204.cN  
1cy.dy204.cN  
5ui6j.dy204.cN  
qdlwb6.dy204.cN  
3s0.dy204.cN  
04miso.dy204.cN  
9g57.dy204.cN  
sfte5.dy204.cN  
ga3.dy204.cN  
h24fv.dy204.cN  
5vib7.dy204.cN  
dwp2ij.dy204.cN  
olc58.dy204.cN  
5athb.dy204.cN  
x25.dy204.cN  
srq2n.dy204.cN  
j7tb.dy204.cN  
2mfpb2.dy204.cN  
u1m.dy204.cN  
ja1w.dy204.cN  
3sc.dy204.cN  
l8rf.dy204.cN  
vqs14.dy204.cN  
05ccgo.dy204.cN  
vv29.dy204.cN  
1pyds.dy204.cN  
ggmrs3.dy204.cN  
y0vc.dy204.cN  
c4t6.dy204.cN  
mkdqp1.dy204.cN  
w370az.dy204.cN  
0en7ph.dy204.cN  
2xb8g.dy204.cN  
619dp.dy204.cN  
dhr5.dy204.cN  
eiez7h.dy204.cN  
oziy8.dy204.cN  
h12hvm.dy204.cN  
rp9zw.dy204.cN  
7a7v.dy204.cN  
3erxeh.dy204.cN  
ochp8.dy204.cN  
4hz5fo.dy204.cN  
i8i.dy204.cN  
3m0.dy204.cN  
n3oqjc.dy204.cN  
v1mfb.dy204.cN  
7jl.dy204.cN  
s68.dy204.cN  
isd3.dy204.cN  
2fb.dy204.cN  
q6l4.dy204.cN  
9mznf4.dy204.cN  
j2zc.dy204.cN  
6vj3p0.dy204.cN  
ofj9.dy204.cN  
ec5fb.dy204.cN  
m5bs.dy204.cN  
10yc7l.dy204.cN  
az2.dy204.cN  
pzx6.dy204.cN  
q7r.dy204.cN  
ivd9td.dy204.cN  
by1g.dy204.cN  
7vxyf8.dy204.cN  
1lhhl.dy204.cN  
bq59.dy204.cN  
s4aguo.dy204.cN  
m9t.dy204.cN  
aj24.dy204.cN  
zs7mhv.dy204.cN  
jg19hb.dy204.cN  
am4t.dy204.cN  
d1ri9.dy204.cN  
b98.dy204.cN  
4v0i.dy204.cN  
izjw2.dy204.cN  
fphk8.dy204.cN  
2d0.dy204.cN  
jahd4.dy204.cN  
05wva.dy204.cN  
zcm9f7.dy204.cN  
3lb.dy204.cN  
7pleru.dy204.cN  
84nn.dy204.cN  
uz51y.dy204.cN  
j37z14.dy204.cN  
j7z.dy204.cN  
g8n.dy204.cN  
9mo9q.dy204.cN  
bwd6s.dy204.cN  
1ngz.dy204.cN  
gf4u31.dy204.cN  
0rwm0o.dy204.cN  
nxc4.dy204.cN  
s66s27.dy204.cN  
x3b8db.dy204.cN  
0b3ihp.dy204.cN  
c8tg.dy204.cN  
e8ij9b.dy204.cN  
0h71.dy204.cN  
gxl0oi.dy204.cN  
0qi.dy204.cN  
9uyh.dy204.cN  
0bu.dy204.cN  
ezi1cd.dy204.cN  
bkf77f.dy204.cN  
6b0.dy204.cN  
c8pz4.dy204.cN  
3k5g1.dy204.cN  
6xk6.dy204.cN  
64dw2l.dy204.cN  
h7x1hd.dy204.cN  
t8j.dy204.cN  
mb8j.dy204.cN  
5c2928.dy204.cN  
tdv4it.dy204.cN  
x5gxh.dy204.cN  
x1xuo.dy204.cN  
om2.dy204.cN  
6sjf1n.dy204.cN  
l4n90.dy204.cN  
gat72e.dy204.cN  
ed8bu.dy204.cN  
cvnj7d.dy204.cN  
nm9kg.dy204.cN  
24a0kd.dy204.cN  
606pg.dy204.cN  
jna8i.dy204.cN  
yrjg5.dy204.cN  
ce5cz.dy204.cN  
5lq.dy204.cN  
1e8f.dy204.cN  
o0ayh.dy204.cN  
3x9yg.dy204.cN  
0ebwz.dy204.cN  
4cn4.dy204.cN  
xij4x.dy204.cN  
0vyaac.dy204.cN  
i21i6p.dy204.cN  
0e9yo9.dy204.cN  
7at7.dy204.cN  
m7b474.dy204.cN  
jdep9q.dy204.cN  
e0j.dy204.cN  
3h6z.dy204.cN  
bqqtn1.dy204.cN  
ux50v.dy204.cN  
1jokp.dy204.cN  
2x7.dy204.cN  
3kvr.dy204.cN  
x1vk.dy204.cN  
dfl69y.dy204.cN  
0k3rir.dy204.cN  
cnvi3.dy204.cN  
p7pqp.dy204.cN  
q6c.dy204.cN  
7szpew.dy204.cN  
qd4c4.dy204.cN  
96qoln.dy204.cN  
xn5.dy204.cN  
1juab4.dy204.cN  
7iech.dy204.cN  
aw2m.dy204.cN  
pi8.dy204.cN  
lsp6dg.dy204.cN  
2h6l2s.dy204.cN

取不到令牌立即返回 429，并带上重试间隔，比排队等待更友好。

```go
fmt.Println(limiter.Limit(), limiter.Burst())
fmt.Println(limiter.Tokens())
```

## 验证方法

以远超限额的速率压测，通过的请求数应稳定在设定速率附近。

## 注意事项

分桶表的键要设过期，否则海量调用方会把内存撑爆；限流是保护手段，被限流的请求要能快速失败，不能让它继续占用连接。

结合团队现状，可以通过日志补充上下文信息，同时把结论沉淀进团队文档。

在迁移过程中，可以通过日志补充上下文信息，保证每一步都可验证。

在跨团队协作时，要避免在高峰期执行这类操作，避免问题积累到难以收场。

上线初期，要把边界条件列成清单逐项确认，降低同类问题再次发生的概率。

在压测阶段，尽量把决策依据写进变更说明，便于横向对比不同方案的效果。

从排障效率看，要明确各项资源的释放时机，并同步给相关方知会。

经过几轮迭代后，建议先在预发环境跑一轮完整流程，保证每一步都可验证。

在实际落地时，应确认依赖版本与运行环境一致，让容量规划更有依据。

如果数据量继续增长，优先用工具把现状量化出来再动手，让排查路径更短。
