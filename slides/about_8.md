## RodaのGoal

* Extensibility
  * Rodaの各機能は全てpluginとして提供されており、ユーザが独自に拡張可能になっている
  * Rodaのcoreは最低限の機能しか提供しておらず、必要な機能(plugin)を自分で追加する必要がある
  * [Roda#Plugins](http://roda.jeremyevans.net/documentation.html#plugins)
* Performance
  * 内部でrouting treeをよしなにキャッシュしており早い(らしい)
