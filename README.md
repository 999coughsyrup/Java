package zong_he_jian_ce;

import java.util.Random;
import java.util.Scanner;

public class AppleGame {

	public static void main(String[] args) {
		@SuppressWarnings("resource")
		Scanner sc = new Scanner(System.in);// 键盘录入命令
		Random rd = new Random();// 随机数生成命令
		System.out.println("好运来苹果机的游戏规则如下：");
		System.out.println("选择水果类型，每次只能选择一种；");
		System.out.println("对你选规则的水果押注；");
		System.out.println("不同水果奖励不同；");
		System.out.println("每个玩家初始赠送10个金币；");
		System.out.println("运转后，若停在你选择的水果上，则获得奖励;否则，你将损失所押的金币；");
		System.out.println("奖励为：所押金币乘以系数，每个水果奖励系数不同，奖励系数如下。");
		System.out.println("猜中的物品和对应的奖励系数如下：");
		System.out.println("苹果-------2");
		System.out.println("木瓜-------5");
		System.out.println("西瓜-------10");
		System.out.println("香蕉-------20");
		System.out.println("橙子-------50");
		System.out.println("葡萄-------100");
		System.out.println("每轮游戏结束后，你可以按Q来退出游戏");
		int money = 10;// 金币,初始为10枚
		int unit = 0;// 水果对应的奖励系数，初始值设为零
		int n = 0;// 所押的金币数
		int b;// 随机整数[范围：1-6]
		String str0 = null;// 玩家输入的水果
		String str1 = null;// 生成的随机整数对应着的水果
		String str2 = null;// 玩家输入的字符与Q对比

		while (true) {
			b = rd.nextInt(6) + 1;// 随机生成1-6的整数
			System.out.println("输入你选择的水果和所押的金币数,下注吧！");
			str0 = sc.next();// 选择的水果
			n = sc.nextInt();// 所押的金币数
			if (money < n) {
				System.out.println("所押的金币数大于你所拥有的金币数，请重新选择");
				continue;
			} else {
				System.out.println("苹果机开始运转，祝你好运");
				switch (b) {
				case 1:
					System.out.println("结果是：---苹果----");
					str1 = "苹果";
					unit = 2;
					break;
				case 2:
					System.out.println("结果是：---木瓜----");
					str1 = "木瓜";
					unit = 5;
					break;
				case 3:
					System.out.println("结果是：---西瓜----");
					str1 = "西瓜";
					unit = 10;
					break;
				case 4:
					System.out.println("结果是：---香蕉----");
					str1 = "香蕉";
					unit = 20;
					break;
				case 5:
					System.out.println("结果是：---橙子----");
					str1 = "橙子";
					unit = 50;
					break;
				case 6:
					System.out.println("结果是：---葡萄----");
					str1 = "葡萄";
					unit = 100;
					break;

				}
				if (str0.equals(str1)) {
					System.out.println("恭喜你，押中了");
					System.out.println("你获得的金币数为" + unit);
					money = money + unit * n;
					System.out.println("你当前的金币数为" + money);
				}

				else {
					System.out.println("很遗憾，手气差");
					System.out.println("你损失的金币数为" + n);
					money = money - n;
					System.out.println("你当前的金币数为" + money);
				}

				if (money < 1) {
					System.out.println("你没有金币了，游戏结束");
					System.exit(0);
				} else {
					System.out.println("如果想退出，请按Q并按回车键,若想继续，请按其他键并按回车键");
					str2 = sc.next();// 让玩家选择(按Q)继续还是退出
					if (str2.equals("Q")) {
						System.out.println("你选择了退出，游戏结束");
						System.exit(0);
					}
					else
						continue;
				}

			}
		}

	}
}
