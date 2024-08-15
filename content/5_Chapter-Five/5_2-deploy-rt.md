---
title: "Task 2:  Deploy a Route Table and Create a UDR"
weight: 4
---





In Task Two, you will deploy a **Route Table** and modify the **Route Table** by associating both protected subnnets to use **port2** of the FortiGate as the default route. This is what is called a **User Defined Route (UDR)**.

- 1. Navigate into your Resource Group and click on the **+ Create** located at the top left of the tool bar.
![](../Images/Azure-creating-vnet.PNG)  

You will be redirected to the Azure Marketplace.

- 2. In the Marketplace search bar, enter **route table** and then enter.  Navigate to the **Route table** offering from Microsoft and select **Create** and **Route table**.
![](../Images/4-2-Azure-deploy-rt-1.PNG)


You will be redirected to the **Create Route table** template.

- 3. Under the **Basics** tab, the **Subscription** and **Resource Groups** should already be filled in with your assigned info.  If not, see the screen shot below for details.
- Under **Instance details**, enter the following:
    - **Region**: "**West US 3**"
    - **Name**: "**Studentxx_RT**" (Replace xx with your assigned student number)
    - **Propagate gateway routes**:  "**No**"
- Select **Next**.
![](../Images/4-2-Azure-deploy-rt-2.PNG)

- 4. On the **Tags** tab, click **Next**.  Nothing to enter here.

- 5. On the **Review + create** tab, confirm your entries under **Basics** and then select **create**.
![](../Images/4-2-Azure-deploy-rt-3.PNG)

- 6. The screen should refresh and you will see **Deployment is in progress**.

- 7. After a few minutes, you will see **Your deployment is complete**.  Select **Go to resource**.  You will be directed to the **Studentxx_RT** Overview page.
![](../Images/4-2-Azure-deploy-rt-4.PNG)

- 8. Take a few moments and familiarize yourselft with the route table **Overview** page.  

**In the next few steps, you will be creating a UDR**
- 9. From the **Studentxx_RT** **Overview** page, navigate to **Settings** and then **Routes**.
From the **Routes** page, select **+ Add**.
![](../Images/4-2-Azure-deploy-rt-5.PNG)

- 10. The **Add route** will display on the right.  Enter the following:
    - **Route name**:  "**Default**"
    - **Destination type**:  "**IP Address**"
    - **Destination IP address/CIDR ranges**:  "**0.0.0.0/0**"
    - **Next hop type**: "**Virtual appliance**"
    - **Next hop address**:  "**192.168.1.36**"  (Confirm this is the same IP assigned to **port2** on your FortiGate NVA).
- Select **Add**
![](../Images/4-2-Azure-deploy-rt-6.PNG)

- 11. You will see the new route called **Default** listed under the **Routes** section.
![](../Images/4-2-Azure-deploy-rt-7.PNG)

- 12. Continue to add two more routes for **Protected-A-Subnet** and **Protected-B-Subnet**.
![](../Images/4-2-Azure-deploy-rt-11.PNG)

- 13. When finished, the **Routes** page should have the three routes listed.  See the following diagram for confirmation.
![](../Images/4-2-Azure-deploy-rt-12.PNG)

- 14. On the left hand side, select **Subnets** and **+ Associate**.  The **Associate subnet** page will display on the right.  Enter the following:
    - **Virtual network**:  "**Studentxx_VNET**"  (Replace xx with your assign student number)
    - **Subnet**: "**Protected-A_Subnet**"
- Select **OK**.
![](../Images/4-2-Azure-deploy-rt-8.PNG)

- 15.  Click **+ Associate** again and add the **Protected-B_Subnet**.  You should have both subnets listed under the **Subnets** tab.
![](../Images/4-2-Azure-deploy-rt-9.PNG)

- 16. Return to the **Overview** page to see a summary of the **Routes** and associated **Subnets**.
![](../Images/4-2-Azure-deploy-rt-10.PNG)

**Continue to Chapter 5 - Task 3: Confirm Linux VMs access via FortiGate**