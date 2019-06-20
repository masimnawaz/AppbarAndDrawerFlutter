# AppbarAndDrawerFlutter
Add Appbar and Navigation Drawer into Flutter App

void main()
{
  runApp(
    MaterialApp(
      debugShowCheckedModeBanner: false,
      home: MyAppBarDrawerApp(),
      theme: ThemeData(
        primaryColor: Colors.lightGreen,
        accentColor: Colors.blue
      ),
    )
  );
}

class MyAppBarDrawerApp extends StatefulWidget {
  @override
  _MyAppBarDrawerAppState createState() => _MyAppBarDrawerAppState();
}

class _MyAppBarDrawerAppState extends State<MyAppBarDrawerApp> {
  final GlobalKey<ScaffoldState> _scaffoldKey = new GlobalKey<ScaffoldState>();
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      key: _scaffoldKey,
      appBar: AppBar(
        title: Text("Appbar Drawer App"),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.search),
            onPressed: (){

            },
          ),
          IconButton(
            icon: Icon(Icons.verified_user),
            onPressed: (){

            },
          ),
        ],
      ),
      drawer: Drawer(
        child: Column(
          children: <Widget>[
            Stack(
              children: <Widget>[
                Image(
                  image: AssetImage("images/header.jpeg")
                ),
                Padding(
                  padding: EdgeInsets.only(top: 30.0, left: 12.0),
                  child: CircleAvatar(
                    radius: 40.0,
                    backgroundImage: AssetImage("images/asim.jpg"),
                  ),
                ),
                Padding(
                  padding: EdgeInsets.only(top: 120.0, left: 12.0),
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: <Widget>[
                      Text("Asim", textDirection: TextDirection.ltr, style: TextStyle(fontWeight: FontWeight.bold, fontSize: 15.0, color: Colors.white)),
                      Text("email@example.com", textDirection: TextDirection.ltr, style: TextStyle(fontSize: 14.0, color: Colors.white),)

                    ],
                  ),
                )
              ],
            ),
            ListView(
              shrinkWrap: true,
              children: <Widget>[
                ListTile(
                  leading: Icon(Icons.home),
                  title: Text("Home"),
                  onTap: (){
                    showInSnackbar("Home");
                  },
                ),
                ListTile(
                  leading: Icon(Icons.star),
                  title: Text("Rate"),
                  onTap: (){
                    showInSnackbar("Rate");
                  },
                ),
                ListTile(
                  leading: Icon(Icons.share),
                  title: Text("Share"),
                  onTap: (){
                    showInSnackbar("Share");
                  },
                ),
              ],
            )
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
        onPressed: (){
          showInSnackbar("Floating Action Button");
        },
      ),
      body: Padding(
        padding: EdgeInsets.only(top: 15.0, left: 12.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Text("Hello World Flutter 1", textDirection: TextDirection.ltr),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Text("Hello World Flutter 2", textDirection: TextDirection.ltr),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Text("Hello World Flutter 3", textDirection: TextDirection.ltr),
            ),

            Image(
              image: AssetImage("images/header.jpg"),
              fit: BoxFit.scaleDown,
            )

          ],
        ),
      ),
    );
  }

  void showInSnackbar(String value)
  {
    _scaffoldKey.currentState.showSnackBar(new SnackBar(content: new Text(value)));
  }
}
