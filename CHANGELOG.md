# Changelog

## v7 WIP

- WrapProcess is replaced with more convenient AddHook that has access to context.Context.
- WithContext no longer creates shallow copy.
- New methods ProcessContext, DoContext, and ExecContext.
- Client respects Context.Deadline when setting net.Conn deadline.
- Client listens on Context.Done while waiting for a connection from the pool.
- Add PubSub.ChannelWithSubscriptions that sends `*Subscription` in addition to `*Message` to allow detecting reconnections.

## v6.15

- Cluster and Ring pipelines process commands for each node in its own goroutine.

## 6.14

- Added Options.MinIdleConns.
- Added Options.MaxConnAge.
- PoolStats.FreeConns is renamed to PoolStats.IdleConns.
- Add Client.Do to simplify creating custom commands.
- Add Cmd.String, Cmd.Int, Cmd.Int64, Cmd.Uint64, Cmd.Float64, and Cmd.Bool helpers.
- Lower memory usage.

## v6.13

- Ring got new options called `HashReplicas` and `Hash`. It is recommended to set `HashReplicas = 1000` for better keys distribution between shards.
- Cluster client was optimized to use much less memory when reloading cluster state.
- PubSub.ReceiveMessage is re-worked to not use ReceiveTimeout so it does not lose data when timeout occurres. In most cases it is recommended to use PubSub.Channel instead.
- Dialer.KeepAlive is set to 5 minutes by default.

## v6.12

- ClusterClient got new option called `ClusterSlots` which allows to build cluster of normal Redis Servers that don't have cluster mode enabled. See https://godoc.org/github.com/osencan/redis#example-NewClusterClient--ManualSetup
