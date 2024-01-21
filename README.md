My library for ASP.NET MVC codefirst DataBase creating (if not exists).
It contains CreateDbIfNotExists generic method.
If we have DbContext class for codefirst, then we can just use DbInitializer.CreateDbIfNotExists<ClassName>(app) in Program.cs
Code example:
  public class MyContext:DbContext
  {
      public MyContext(DbContextOptions<MyContext> options) : base(options)
      {
      }
      public DbSet<User>? Users { get; set; }
      public DbSet<Plane>? Planes { get; set; }
      public DbSet<Flight>? Flights { get; set; }
      public DbSet<Seat>? Seats { get; set; }
  }
 
 Program.cs:
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddControllersWithViews();
var app = builder.Build();

DbInitializer.CreateDbIfNotExists<MyContext>(app); // <------

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Home/Error");
    app.UseHsts();
}
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthorization();
app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=HomePage}/{id?}");
app.Run();
