# .pb-to-.mcap-to-pcd

1. .pb to .mcap
---------------------------


labi@lb:~/
     
    ros2_ws$ source install/setup.bash 

labi@lb:

    ~/ros2_ws$ colcon build --symlink-install


    ros2 run pb_to_ros2_bag pb_to_mcap \ /home/labi/ws_livox/a13/data_2025-12-17-14-41-21


or

    ros2 run pb_to_ros2_bag pb_to_mcap \
      ~/ws_livox/a13/data_2025-12-17-14-41-21



2. .mcap to .pcd

    cd ~/ws_livox
    colcon build --packages-select pcd_saver
    source install/setup.bash

    
2️⃣ Verify ROS can see the executable
bash
Copy code
ros2 pkg executables pcd_saver
✅ Expected output
nginx
Copy code
pcd_saver_custommsg
If you see this → everything is wired correctly.

3️⃣ Run your node (THIS is the correct command)
bash
Copy code


    ros2 run pcd_saver pcd_saver_custommsg


You should see:

css
Copy code
[INFO] Saving PCD frames to /home/labi/pcd_output
✅ Final MCAP → PCD conversion
Terminal 1
bash
Copy code


    source ~/ws_livox/install/setup.bash
    ros2 run pcd_saver pcd_saver_custommsg


Terminal 2
bash
Copy code

    source ~/ws_livox/install/setup.bash
    cd ~/ws_livox/a13/a13_ros2_mcap1
    ros2 bag play a13_ros2_mcap_0.mcap




