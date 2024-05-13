

# PlayableDirector(最上层Component)

## PlayableAssets(Component上的时间轴资产)

### outputs(这里其实是bind 即所有资产上所有轨道的集合)

#### bind(即单个轨道的绑定信息集合) 包含了 需要绑定的物体和bing的名字

#### bind.sourceObject as T(TrackAsset) 即轨道本身所包含的信息

##### Clip (bind.sourceObject.GetClips() 即获取所有轨道内的clip
