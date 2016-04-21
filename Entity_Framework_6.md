##EF6 Detach & Attach:
https://msdn.microsoft.com/en-us/library/bb896271%28v=vs.100%29.aspx
	
* System.Data.Objects.ObjectContext.Detach(System.Object) 
* System.Data.Objects.ObjectContext.Detach(Object entity)
* System.Data.Objects.ObjectSet<TEntity>.Detach(TEntity entity)

###EF6 Detach recursively:
http://www.codemag.com/article/0907071

##EntityDataSource:
Namespace:   System.Web.UI.WebControls
Assembly:  System.Web.Entity (in System.Web.Entity.dll)
https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.entitydatasource%28v=vs.110%29.aspx

###Validate:
* public event EventHandler<EntityDataSourceChangingEventArgs> Inserting
* public event EventHandler<EntityDataSourceChangingEventArgs> Updating

###Status:
* public event EventHandler<EntityDataSourceChangedEventArgs> Inserted
* public event EventHandler<EntityDataSourceChangedEventArgs> Updated

###EntityDataSourceChangingEventArgs Class
https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.entitydatasourcechangingeventargs%28v=vs.110%29.aspx

###EntityDataSourceChangedEventArgs Class
https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.entitydatasourcechangedeventargs%28v=vs.110%29.aspx

##Security:
https://msdn.microsoft.com/en-us/library/cc668189%28v=vs.100%29.aspx
https://msdn.microsoft.com/en-us/library/ecb3hak0%28v=vs.100%29.aspx

##Misc:
https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.entitydatasource_events%28v=vs.110%29.aspx
