My library for ASP.NET MVC(.net 7.0) codefirst DataBase creating (if not exists), 
that contains CreateDbIfNotExists generic method.
If we have DbContext class for codefirst, then we can just use DbInitializer.CreateDbIfNotExists<ClassName>(app) in Program.cs (remember to use builder.Services.AddDbContext or builder.Services.AddDbContextPool before)
