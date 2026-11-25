# 价格策略服务日志按大小切分并保留最近几份

<!-- content-workspace-job:dab9dfd7-d697-4aaf-a2dc-2ebebb6e7cc0 -->

## 问题场景

价格策略服务长期运行，日志文件涨到几十 GB，出问题时打不开也传不走。

## 实现步骤

配置 RotatingFileHandler，指定单文件上限与保留份数。

```python
import logging
from logging.handlers import RotatingFileHandler

def logger(name="price"):
    lg = logging.getLogger(name)
    lg.setLevel(logging.INFO)
```

统一格式包含时间、级别、模块与追踪号，方便按 trace 聚合。

```python
    h.setFormatter(logging.Formatter(
        "%(asctime)s %(levelname)s [%(name)s] %(message)s"))
    lg.addHandler(h)
    lg.propagate = False
    return lg
```

douyindz.cN  
www.douyindz.cN  
po67.douyindz.cN  
az7h66.douyindz.cN  
kzs5l.douyindz.cN  
sq4.douyindz.cN  
di3ci.douyindz.cN  
n2tyw.douyindz.cN  
2zxq1.douyindz.cN  
2qhw98.douyindz.cN  
5ozsq.douyindz.cN  
kfsk86.douyindz.cN  
q3w.douyindz.cN  
kz2j.douyindz.cN  
qa58v7.douyindz.cN  
28z.douyindz.cN  
62vjg.douyindz.cN  
ci821r.douyindz.cN  
h3b.douyindz.cN  
lbc0k.douyindz.cN  
q967.douyindz.cN  
sg8v.douyindz.cN  
qvnd7.douyindz.cN  
84vmuc.douyindz.cN  
7v3o7.douyindz.cN  
r4l1.douyindz.cN  
o5e.douyindz.cN  
flz9z.douyindz.cN  
x049b.douyindz.cN  
47oxt.douyindz.cN  
dlf0.douyindz.cN  
4rxxx.douyindz.cN  
n19x.douyindz.cN  
0vew6.douyindz.cN  
xx93un.douyindz.cN  
xay7n.douyindz.cN  
8kdf.douyindz.cN  
964why.douyindz.cN  
mhc0lc.douyindz.cN  
x87v.douyindz.cN  
h59x.douyindz.cN  
z6ob.douyindz.cN  
7ew.douyindz.cN  
na0j.douyindz.cN  
itp76.douyindz.cN  
5w64.douyindz.cN  
2xsm.douyindz.cN  
8xsq.douyindz.cN  
x95n.douyindz.cN  
4t5m.douyindz.cN  
7xwm73.douyindz.cN  
ts4w.douyindz.cN  
x6lu.douyindz.cN  
fk3q.douyindz.cN  
1epete.douyindz.cN  
nyv912.douyindz.cN  
iaf6l.douyindz.cN  
cj0f.douyindz.cN  
ak7y.douyindz.cN  
vu3rot.douyindz.cN  
x5b76.douyindz.cN  
f821uk.douyindz.cN  
i4hv7.douyindz.cN  
cz7.douyindz.cN  
00a8t.douyindz.cN  
5cd9ks.douyindz.cN  
jjd2.douyindz.cN  
6itbw.douyindz.cN  
ed7uud.douyindz.cN  
7sg.douyindz.cN  
xl3hiq.douyindz.cN  
f1dv.douyindz.cN  
9dy56b.douyindz.cN  
6wo58.douyindz.cN  
de1.douyindz.cN  
41rb.douyindz.cN  
obm4.douyindz.cN  
qdij4.douyindz.cN  
i4uua.douyindz.cN  
h4wm.douyindz.cN  
474lq.douyindz.cN  
q0df.douyindz.cN  
koc465.douyindz.cN  
hb6pd.douyindz.cN  
g3m1cn.douyindz.cN  
2lc.douyindz.cN  
ha4x.douyindz.cN  
o6n12q.douyindz.cN  
2yk9.douyindz.cN  
b4k79.douyindz.cN  
dyc3ag.douyindz.cN  
6xfa.douyindz.cN  
u1e.douyindz.cN  
ta0.douyindz.cN  
5d792.douyindz.cN  
xu059y.douyindz.cN  
14gfit.douyindz.cN  
ht4k.douyindz.cN  
80e8e.douyindz.cN  
zgo85e.douyindz.cN  
2g0bw.douyindz.cN  
pbah2.douyindz.cN  
5oi2py.douyindz.cN  
38b.douyindz.cN  
7tb.douyindz.cN  
ff9o.douyindz.cN  
be07jz.douyindz.cN  
lqgc3.douyindz.cN  
mhvh5.douyindz.cN  
9be.douyindz.cN  
9rkqp.douyindz.cN  
r3d4dx.douyindz.cN  
rzfz5.douyindz.cN  
kf4n.douyindz.cN  
aex3m.douyindz.cN  
0dx8j.douyindz.cN  
uz4l4.douyindz.cN  
6zt6.douyindz.cN  
c2f.douyindz.cN  
00b.douyindz.cN  
dyws33.douyindz.cN  
5vypg1.douyindz.cN  
hiwi8.douyindz.cN  
16f6.douyindz.cN  
a7ka7.douyindz.cN  
i3zrm.douyindz.cN  
o13ra.douyindz.cN  
b39rv0.douyindz.cN  
nhwv6.douyindz.cN  
o4esd.douyindz.cN  
2eg486.douyindz.cN  
8f3awe.douyindz.cN  
m01en.douyindz.cN  
yd7ymc.douyindz.cN  
j4m6.douyindz.cN  
8ue8.douyindz.cN  
2f7h.douyindz.cN  
c4f2e.douyindz.cN  
titeo5.douyindz.cN  
3r67.douyindz.cN  
7db.douyindz.cN  
eny0.douyindz.cN  
10hr.douyindz.cN  
nhv34.douyindz.cN  
7sc7n.douyindz.cN  
v7b.douyindz.cN  
7zdr61.douyindz.cN  
nz6dc.douyindz.cN  
6fyngn.douyindz.cN  
2pu.douyindz.cN  
8g1.douyindz.cN  
e88.douyindz.cN  
0im.douyindz.cN  
ik9l.douyindz.cN  
v4j.douyindz.cN  
2jn8g.douyindz.cN  
i9u9a.douyindz.cN  
2yuj8.douyindz.cN  
467l.douyindz.cN  
mre8p.douyindz.cN  
w921l.douyindz.cN  
bpm7kq.douyindz.cN  
z2isj.douyindz.cN  
fk95.douyindz.cN  
e9uf.douyindz.cN  
4s3.douyindz.cN  
o0y.douyindz.cN  
76pjia.douyindz.cN  
0fs.douyindz.cN  
q4cv9.douyindz.cN  
umgs0.douyindz.cN  
d2x.douyindz.cN  
4bs6.douyindz.cN  
ab6az.douyindz.cN  
4po.douyindz.cN  
iq3n.douyindz.cN  
16a.douyindz.cN  
3ap9qr.douyindz.cN  
fqke9.douyindz.cN  
q5sqaw.douyindz.cN  
u91x2j.douyindz.cN  
0zar.douyindz.cN  
zy8ct.douyindz.cN  
5sgc.douyindz.cN  
1v0cv.douyindz.cN  
g6o7ur.douyindz.cN  
vg7js2.douyindz.cN  
7rdh6j.douyindz.cN  
g0tbf.douyindz.cN  
rf7.douyindz.cN  
3dzf3.douyindz.cN  
z8j.douyindz.cN  
0rh.douyindz.cN  
op553.douyindz.cN  
5bdmmd.douyindz.cN  
u04n9a.douyindz.cN  
qk6h.douyindz.cN  
81sbe.douyindz.cN  
4vutyc.douyindz.cN  
1mk2.douyindz.cN  
av0l0.douyindz.cN  
75hle.douyindz.cN  
jd0.douyindz.cN  
6vbqx.douyindz.cN  
4kl.douyindz.cN  
jf6wi5.douyindz.cN  
y8sgd2.douyindz.cN  
m2i.douyindz.cN  
aq0g0.douyindz.cN  
62yoj.douyindz.cN  
cngo5b.douyindz.cN  
pqv8nn.douyindz.cN  
88x28.douyindz.cN  
s2ers1.douyindz.cN  
zb975.douyindz.cN  
s7t9g.douyindz.cN  
t5wx.douyindz.cN  
qt5.douyindz.cN  
gwg7l.douyindz.cN  
g0bgw.douyindz.cN  
y8a.douyindz.cN  
1ln.douyindz.cN  
37v.douyindz.cN  
md36.douyindz.cN  
nnyx9.douyindz.cN  
qsrm9.douyindz.cN  
h5kjz.douyindz.cN  
b5rad.douyindz.cN  
m1v3xi.douyindz.cN  
u13ae.douyindz.cN  
wl2kks.douyindz.cN  
vc26u.douyindz.cN  
va9.douyindz.cN  
uv3eg1.douyindz.cN  
4n0zh.douyindz.cN  
1334h.douyindz.cN  
1ku.douyindz.cN  
5rtcjl.douyindz.cN  
7cuwg.douyindz.cN  
gim5io.douyindz.cN  
1fd7cr.douyindz.cN  
gm4dp4.douyindz.cN  
n6mi86.douyindz.cN  
xajh58.douyindz.cN  
s8vviz.douyindz.cN  
ykx3.douyindz.cN  
x9tu.douyindz.cN  
z5zfq.douyindz.cN  
m3w9qa.douyindz.cN  
ryvr5p.douyindz.cN  
7gq4t3.douyindz.cN  
4mc.douyindz.cN  
4i52y4.douyindz.cN  
ew8dav.douyindz.cN  
rp0.douyindz.cN  
q2mgw.douyindz.cN  
z03.douyindz.cN  
26juw.douyindz.cN  
ywzd9k.douyindz.cN  
0frb4o.douyindz.cN  
2q43.douyindz.cN  
ds3l.douyindz.cN  
9hn4.douyindz.cN  
na5ls.douyindz.cN  
ca9.douyindz.cN  
00qc1.douyindz.cN  
5gx5u1.douyindz.cN  
h7wah1.douyindz.cN  
k4h1gt.douyindz.cN  
pb7l.douyindz.cN  
d09.douyindz.cN  
ym53f.douyindz.cN  
ymh09.douyindz.cN  
io9z.douyindz.cN  
e69q.douyindz.cN  
5tc.douyindz.cN  
e4723.douyindz.cN  
7yj0.douyindz.cN  
q4lv9.douyindz.cN  
tpf7bo.douyindz.cN  
f8ms.douyindz.cN  
82j.douyindz.cN  
q0e.douyindz.cN  
o5lb.douyindz.cN  
i3imh6.douyindz.cN  
2lnq6.douyindz.cN  
j5q3.douyindz.cN  
48g.douyindz.cN  
1ock.douyindz.cN  
s5l.douyindz.cN  
jvb7du.douyindz.cN  
oy4i.douyindz.cN  
zs7y.douyindz.cN  
h5d.douyindz.cN  
9t3q6.douyindz.cN  
q41ggc.douyindz.cN  
a312n8.douyindz.cN  
mlug58.douyindz.cN  
c53ub.douyindz.cN  
i0t.douyindz.cN

启动时打印一次生效配置，确认处理器没被框架的默认配置覆盖。

```python
lg = logger()
for i in range(2000):
    lg.info("write %d", i)
print("handlers", len(lg.handlers))
```

## 验证方法

把上限调到极小值并连续写日志，观察目录中文件数量是否稳定在保留份数加一。

## 注意事项

多进程同时写同一文件时轮转会互相踩，需改用 WatchedFileHandler 配合外部切割；propagate 未关闭会出现重复行。

在迁移过程中，可以通过日志补充上下文信息，同时把结论沉淀进团队文档。

结合团队现状，可以通过日志补充上下文信息，保证每一步都可验证。

在资源受限的环境下，要避免在高峰期执行这类操作，避免问题积累到难以收场。

在实际落地时，建议先在小流量环境验证行为是否符合预期，以便快速定位瓶颈。

经过几轮迭代后，需要同时关注错误率与延迟两个指标，便于横向对比不同方案的效果。

上线初期，要把异常路径和正常路径分别覆盖一遍，并同步给相关方知会。

经过几轮迭代后，建议先在预发环境跑一轮完整流程，避免问题积累到难以收场。

从长期维护角度看，优先保证失败时能快速定位原因，以便快速定位瓶颈。

从可观测性角度，应确认依赖版本与运行环境一致，防止出现隐性回归。
