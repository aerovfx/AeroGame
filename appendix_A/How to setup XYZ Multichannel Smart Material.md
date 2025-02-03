Sử dụng XYZ Multichannel Smart Materia
Phân tích về multichannel 
Utility Map: Sử dụng kênh Blue để sử dụng cho Cavity map vì lí do lấy micro AO với bản đồ dịch chuyển Displacement khá là khó khăn.
![1](https://github.com/user-attachments/assets/e122af01-10a1-444b-a4a9-4661af827ed6)
![22](https://github.com/user-attachments/assets/950ae95b-98dc-4f3a-bb94-982551f39b73)
Multi-channel Displacement

Bản đồ dịch chuyển thể hiện thông tin "chiều cao" sẽ cho phép lưới được xếp/chia nhỏ và có được mức độ chi tiết siêu cao tại thời điểm kết xuất.

Bản đồ dịch chuyển đa kênh của chúng tôi, còn được gọi là bản đồ đóng gói kênh, cực kỳ hữu ích khi cần có được sự linh hoạt cao độ trong thời gian kết xuất.

Tính năng đa kênh hoàn toàn mới này chỉ có trên các gói VFace là hoàn toàn bổ sung, nghĩa là tất cả các tần số này là độc lập và duy nhất trên các kênh. Nói cách khác: Không có dữ liệu chồng chéo giữa các kênh Đỏ, Xanh lục và Xanh lam.

Thông tin của bản đồ float exr 32 bit này được lưu trữ vào kênh màu đỏ và phải được chuẩn hóa trong khoảng 0-1 (với sai số 5%).

Kết quả là, một bản đồ dịch chuyển đa kênh 16k chất lượng cao đã sẵn sàng để sử dụng!

![3](https://github.com/user-attachments/assets/f569238e-768a-41b6-bb6f-adc1a4e9f82c)
Fully calibrated Displacement
Bản đồ dịch chuyển thể hiện thông tin "chiều cao" sẽ cho phép lưới được xếp/chia nhỏ và có được mức độ chi tiết siêu cao tại thời điểm kết xuất.

Bản đồ dịch chuyển của chúng tôi đã được hiệu chỉnh hoàn toàn dựa trên lưới mà chúng tôi cung cấp để có được thông tin chiều cao hoàn hảo trực tiếp mà không cần phải điều chỉnh bất kỳ giá trị trọng lượng nào trước khi kết xuất.

Là điểm khởi đầu, các bản đồ dịch chuyển VFace này đã được tạo ra từ việc chụp ảnh các tài năng, được làm sạch và nâng cao bằng các công nghệ tiên tiến nhất của chúng tôi là Hyperclean và Hyperskin.

Thông tin của bản đồ float exr 32 bit này được lưu trữ vào kênh màu đỏ, chứa cả giá trị âm và dương.
![4](https://github.com/user-attachments/assets/d9d84056-b986-496e-b1ef-22499a54c041)
2. Substance Painter
![5](https://github.com/user-attachments/assets/115df039-8597-4112-9209-8fabf4481bfb)
![6](https://github.com/user-attachments/assets/47ee1a14-c9e1-4f60-8e51-05236497d377)
![7](https://github.com/user-attachments/assets/f4693338-22de-4387-b43c-3cfb1c28c4c0)
![8](https://github.com/user-attachments/assets/64c4d224-a4d7-464d-b1f5-8bdfcd91dc4a)
//IGNORE THE RED LAYER IN THE SMART MATERIAL, THESE ARE ONLY USER INFO//

START: Open in Photoshop the Multichannel Face Displace.TIF file and exctract the R-G-B channels
(to exctract a channel: go to Channel palette, select a single channel, CTRL+A to select all the img, CTRL+C to copy, create a new project in File-> New.., click Create, and CTRL+V in a layer, done!)
       Save these as .PNG format
       Do the same with Utility.TIF, save these as .PNG format
       Convert the FullFace Albedo.TIF in .PNG
* to avoid crash or slow down the Substance Painter too much, I suggest reducing the ALL the XYZ Multichannel maps size by 25% in Photoshop * 

1. Import the XYZ MultiChannel for SubstancePainter.spsm in Substance Painter
2. Import single MultiChannel files as .PNG in Substance Painter
3. In the TEXTURE SET SETTINGS menu create new Channels, click on + sign and add User0, User2, User3 (the User channels must be exactly these!) in L16.
4. Select the Projection Tool (shortcut key 3) and leave only the following channels active: color, user0, user2, user3
5. Assaing the maps in the following order:
     Base Color = Albedo 
     User0 = Displacement map (Photoshop Channel R)
     User2 = Secondary map (Photoshop Channel G)
     User3 = Tertiary map (Phothoshop Channel B)
     User4 = Hemoglobin (Photoshop Channel R)
     User5 = Melanin (Photoshop Channel G)
     User6 = Specular (Photoshop Channel B)
5. Navigate to the yellow layer (Texture XYZ) and select the Paint "PROJECTION TOOL HERE". Start projection your maps, ONLY on this layer. 
6. Activate the purple layers to check your projected displacement maps on the mesh.
   Change the intensity of a single displacement map (Displacement, Secondary, Tertiary) by selecting the layer and changing the Anchor point Levels. Be aware to only change the lower WHITE value.
7. Activate the green layers to cover the Base Color with a simple Lambert material, or add a simple Roughness choosing one of the 2 types.
8. Activate the blue layers if you need to change the color of the BaseColor (skin), using the Melanin or the Hemoglobin layer.


The resulting Height detail can be exported with any Output Template.
This Smart Material keeps baked Normal Map detail, NO OVERRIDE.

This plugin was tested with XYZ Multichannel Faces maps (https://texturing.xyz/collections/multi-channel-faces). 
Test done in Substance Painter 2020.2.2 (6.2.2)
Texture Set Size used: 2048x2048 (upscalable during Texture Export)


1.	Nuke -> Zbrush
