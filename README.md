# ProLinq

This repository is a copy of: http://prolinq.codeplex.com/

I create a copy because CodePlex is near to be closed.

About

ProLinq is a library with IQueryable extensions and tools. It aims to help using IQueryable in business applications, giving you more control over it.

What's new

3/10/2013  
ProLinq is updated.
Added configuration options
Added fluent configuration API
ProLinq.Wcf is released. See documentation.
Quick preview

Wcf
ProLinq.Wcf allows you to use IQueryable in your WCF web services.
var prods = channel.GetProducts().Where(p => p.CategoryId == 1).OrderByDescending(a => a.Price).Take(3);
Read more about using ProLinq.Wcf.
Projection
ProLinq can project IQueryable sources on it's own, meaning it doesn't rely on the source provider to do it. This gives you more freedom on types of objects you are projecting to. You can easly write something like:
IQueryable<BusinessProduct> businessProducts = products.Project().To<BusinessProduct>(p => new BusinessProduct(p)); 
Read more about using Projection.
Interception
ProLinq can also intercept query execution for purposes of logging, result replacement and etc.
IQueryable<Product> products = ProductRepository.Get();
products.Intercept(q =>
		{
			Trace.WriteLine("ProductRepository is being queried: " + q.Expression.ToString());
			return q.Execute();
		});
Read more about using Interception.
Installation

You can download bins here or install using NuGet:
Install-Package ProLinq
Install-Package ProLinq.Wcf
