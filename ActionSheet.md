# Action sheet build with swiftUI

is action sheet build with swiftUI for render array of strings option for user.
Worked and tested for iphone only untill now.


# At final you should have something like this:- 

![Screenshot](https://github.com/ragaie/SwiftUI-Component/blob/master/Screen%20Shot%202020-09-02%20at%2012.01.45%20PM.png)



## How to add it to Your Project :-

1- create new file name PickerView.swift

2- copy and paste down code inside it
```
//
//  PickerView.swift
//  Welcome_To_SwiftUI
//
//  Created by Ragaie Alfy on 8/31/20.
//  Copyright © 2020 Ragaie Alfy. All rights reserved.
//

import SwiftUI
struct PickerView: View {
    var items : [String] //= []
    @Binding  var selecteditem : Int
    @Binding  var isHidden : Bool

    var hight = UIScreen.main.bounds.height / 3.5
    var body: some View {
        VStack{
            Rectangle().foregroundColor(.black).opacity(0.7).padding(.bottom, -40)
                .onTapGesture {
                    self.isHidden = false

                }
            
            
            ZStack{
                VStack{
                    RoundedRectangle(cornerRadius: 3).foregroundColor(.gray).frame(width: 60, height:6, alignment: .center)
                    RoundedRectangle(cornerRadius: 15).foregroundColor(.white)
                }
                  VStack{
                    Button(action: {
                        self.isHidden = false
                    }) {
                        HStack{
                            Text(NSLocalizedString("Done", comment: "")).font(.system(size: 17)).foregroundColor(.black).padding(.leading, 20).padding(.top, 30)
                            Rectangle().foregroundColor(.clear)
                        }
                    }.padding(.bottom, -30)

                    HStack{
                    Rectangle().foregroundColor(.clear).frame( height: 10)

                        Picker("", selection: $selecteditem) {
                        ForEach(0 ..< items.count) {
                            Text(self.items[$0])
                        }
                        
                        }.foregroundColor(.black).pickerStyle(WheelPickerStyle())
                    Rectangle().foregroundColor(.clear).frame( height: 10)
                    }
                }
            }.clipShape(RoundedRectangle(cornerRadius: 15), style: .init(eoFill: false, antialiased: false)).padding(.bottom, -12).frame( height: hight)
        }
    }
}

struct PickerView_Previews: PreviewProvider {
    static var previews: some View {
        PickerView(items: [], selecteditem: .constant(0), isHidden: .constant(true))
    }
}

```

# How add it to your Screen need it:-

```
struct <yourSreenView>: View {
    @State var selecteditem : Int  = 0
    @State var selectedvalue : String  = ""

    @State var showPicker : Bool = false
    var items  = ["select your option","first item","secand item","third item"]
    var body: some View {
        
        ZStack{
                
            VStack{
                Text("SwitUI - Chtar").padding(.all, 50)
                Spacer()
                        Button(action: {
                            self.showPicker = !self.showPicker
                        }) {
                              Text("ShowPicker").font(.body)
                        }
                Text(selectedvalue).padding(.all, 10)

                Spacer()
            }
            if self.showPicker {
                
                PickerView(items: items,selecteditem: $selecteditem, isHidden: $showPicker)
                    //to publish you value item not index
                    .onReceive([self.selecteditem].publisher) { index in
                    self.selectedvalue = self.items[index]
                }
                
            }
   
        }.edgesIgnoringSafeArea(.all)
}
}

```




## Author

* **Ragaie alfy Fahmey**  - [ragaie](https://github.com/ragaie)

## You can find me in linked in 
- [Ragaie alfy](www.linkedin.com/in/ragaie-alfy)

