# 生命周期 

## Mounting 挂载 (渲染到DOM中)

- constructor
- componentWillMount 组件即将挂载
- render
- componentDidMount  组件完成挂载

## Updating 更新

- componentWillReceiveProps(newPorps) 父组件更新，接收到父组件传递过来的新的props
- shouldComponentUpdate(newPorps,newState) return true|false 是否更新
- componentWillUpdate(newProps,newState) 即将更新组件
- render()
- componentDidUpdate() 更新完成

## Unmounting 卸载 (从DOM中删除)

- componentWillUnmount() 即将卸载
