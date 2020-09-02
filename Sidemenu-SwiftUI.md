#Side menu with swiftUI

this tested for iphone and english version only, still under devvelopment 




# Real life app example acreen shot:- 

![Screenshot](https://github.com/ragaie/SwiftUI-Component/blob/master/Screen%20Shot%202020-09-02%20at%205.33.35%20PM.png)


# how can you add it 

1- create file MainView.swift

2- paste this code inside it

```
//
//  MainView.swift
//  Welcome_To_SwiftUI
//
//  Created by Ragaie Alfy on 8/25/20.
//  Copyright © 2020 Ragaie Alfy. All rights reserved.
//

import SwiftUI

struct MainView: View {
    @State var showMenu = false
    
    var body: some View {
        GeometryReader { geometry in
         //   NavigationView{

            ZStack {

                HomePageView(showMenu: self.$showMenu)
                    .frame(width: geometry.size.width, height: geometry.size.height)
                    .offset(x: self.showMenu ? geometry.size.width/1.5 : 0)
               
                if self.showMenu {
                    HStack{
                        SideMenuView().frame(width:  geometry.size.width/1.5 , height: geometry.size.height )
                        Rectangle().foregroundColor(.clear)
                    }.animation(.spring())
            
                }
              
            }
            }
        }
    
}


struct MainView_Previews: PreviewProvider {
    static var previews: some View {
        MainView()
    }
}

```



3- create HomePageView.file for you home screen


```
struct HomePageView1: View {
    @Binding var showMenu :Bool

    var body: some View {
        //show loader above all content

        VStack{
            HStack{
                ZStack{
                    HStack{
                        Button(action: {
                            withAnimation {
                                          self.showMenu = !self.showMenu
                                       }
                        }) {
                           Text("Open")
                        }
                        Rectangle().foregroundColor(.clear).frame(height: 30)
                        
                    }
                    Rectangle().foregroundColor(.clear).frame(height: 30)
                }
                Spacer()
                Text("Main View").frame(width: 70, height: 30, alignment: .center).padding(.top, 10)
                Spacer()
                
                Rectangle().foregroundColor(.clear).frame(height: 30)
                
                Spacer()
            }

            
            ScrollView{
             //   LoadingView(isShowing: $viewModel.showLoader) {
                    
                    VStack{
                     //   if self.viewModel.showLoader == false{
                          Text("HIT Button")
                    }
            //    }
            }
            
              
            }.background(Color.white)
        }
    }
```


4- add side menu view  SideMenuView.swift :- 
```

//
//  SideMenuView.swift
//  Welcome_To_SwiftUI
//
//  Created by Ragaie Alfy on 8/25/20.
//  Copyright © 2020 Ragaie Alfy. All rights reserved.
//

import SwiftUI

struct SideMenuView: View {
    var body: some View {
            
            VStack {
                ScrollView( showsIndicators: false, content: {
                    VStack{
                        ForEach(< !!!!!>items, id: \.id) { item  in
                            Text("Side menu")
                        }
                    }
                })
            
            
       
            }.padding(.bottom, 10)
            
        }.padding()
            .background(Color.white)
            .clipped()
            .shadow(color: Color.red, radius: 10, x: 0, y: 0).edgesIgnoringSafeArea(.all)
        
    }
}

struct SideMenuView_Previews: PreviewProvider {
    static var previews: some View {
        SideMenuView()
    }
}

```





## Author

* **Ragaie alfy Fahmey**  - [ragaie](https://github.com/ragaie)

## You can find me in linked in 
- [Ragaie alfy](www.linkedin.com/in/ragaie-alfy)
