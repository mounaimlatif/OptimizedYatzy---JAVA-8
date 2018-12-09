/**
 * Optimized by Mounaim LATIF 
 */
package com.orange.shine2mesh.acceptance;

import java.util.Arrays;
import java.util.Comparator;
import java.util.List;
import java.util.Optional;
import java.util.stream.Collectors;

public class Yatzy {

	private List<Integer> dice;

	public Yatzy(int d1, int d2, int d3, int d4, int d5) {
		dice = Arrays.asList(d1, d2, d3, d4, d5);
	}

	public static int chance(int d1, int d2, int d3, int d4, int d5) {
		return d1 + d2 + d3 + d4 + d5;
	}

	public static int yatzy(Integer... dice) {
		List<Integer> diceList = Arrays.asList(dice);
		final int value = diceList.get(0);
		return diceList.stream().filter(d -> d == value).collect(Collectors.toList()).size() == diceList.size() ? 50 : 0;
	}

	public static int spear(Integer valueSpear, int d1, int d2, int d3, int d4, int d5) {
		return Arrays.asList(d1, d2, d3, d4, d5).stream().filter(val -> val == valueSpear).mapToInt(Integer::intValue).sum();
	}

	private int spearInterne(Integer spearValue) {
		return dice.stream().filter(die -> die == spearValue).mapToInt(i -> i.intValue()).sum();
	}

	/**
	 * cores the sum of the two highest matching dice
	 * 
	 * @param numberOfPair
	 * @param d1
	 * @param d2
	 * @param d3
	 * @param d4
	 * @param d5
	 * @return
	 */
	private static int pair(int numberOfPair, int d1, int d2, int d3, int d4, int d5) {
		List<List<Integer>> listOfPair = Arrays.asList(d1, d2, d3, d4, d5).stream()
				.collect(Collectors.groupingBy(Integer::intValue)).values().stream().filter(ll -> ll.size() >= 2).collect(Collectors.toList());
		if (!listOfPair.isEmpty())
			return listOfPair.stream().sorted(new Comparator<List<Integer>>() {

				@Override
				public int compare(List<Integer> o1, List<Integer> o2) {
					return o2.get(0).compareTo(o1.get(0));
				}
			}).limit(numberOfPair).map(l -> l.subList(0, 2).stream().mapToInt(Integer::intValue).sum()).collect(Collectors.toList()).stream()
					.mapToInt(Integer::intValue)
					.sum();
		return 0;
	}

	public static int score_pair(int d1, int d2, int d3, int d4, int d5) {
		return pair(1, d1, d2, d3, d4, d5);
	}

	public static int two_pair(int d1, int d2, int d3, int d4, int d5) {
		return pair(2, d1, d2, d3, d4, d5);
	}

	/**
	 * If there are three dice with the same number, the player scores the sum
	 * of these dice
	 * 
	 * @param x
	 * @param d1
	 * @param d2
	 * @param d3
	 * @param d4
	 * @param d5
	 * @return
	 */
	private static int xOfkind(int x, int d1, int d2, int d3, int d4, int d5) {
		List<Integer> diceList = Arrays.asList(d1, d2, d3, d4, d5);
		List<List<Integer>> listGrouped = diceList.stream()
				.collect(Collectors.groupingBy(Integer::intValue)).values().stream().collect(Collectors.toList());
		if (!listGrouped.isEmpty()) {
			Optional<List<Integer>> list = listGrouped.stream().sorted(new Comparator<List<Integer>>() {

				@Override
				public int compare(List<Integer> o1, List<Integer> o2) {
					return o2.get(0).compareTo(o1.get(0));
				}
			}).filter(l -> l.size() >= x).findFirst();
			if (list.isPresent())
				return list.get().subList(0, x).stream().mapToInt(Integer::intValue).sum();
		}
		return 0;
	}

	public static int four_of_a_kind(int _1, int _2, int d3, int d4, int d5) {
		return xOfkind(4, _1, _2, d3, d4, d5);
	}

	public static int three_of_a_kind(int d1, int d2, int d3, int d4, int d5) {
		return xOfkind(3, d1, d2, d3, d4, d5);
	}

	public static int smallStraight(int d1, int d2, int d3, int d4, int d5) {
		return Arrays.asList(d1, d2, d3, d4, d5).containsAll(Arrays.asList(1, 2, 3, 4, 5)) ? 15 : 0;
	}

	public static int largeStraight(int d1, int d2, int d3, int d4, int d5) {
		return Arrays.asList(d1, d2, d3, d4, d5).containsAll(Arrays.asList(2, 3, 4, 5, 6)) ? 20 : 0;
	}

	/**
	 * If the dice are two of a kind and three of a kind, the player scores the
	 * sum of all the dice
	 * 
	 * @param d1
	 * @param d2
	 * @param d3
	 * @param d4
	 * @param d5
	 * @return
	 */
	public static int fullHouse(int d1, int d2, int d3, int d4, int d5) {
		int twoofKindValue = xOfkind(2, d1, d2, d3, d4, d5);
		int threeofKindValue = xOfkind(3, d1, d2, d3, d4, d5);
		return (twoofKindValue != 0 && twoofKindValue != 0) ? twoofKindValue + threeofKindValue : 0;
	}

	public static int ones(int d1, int d2, int d3, int d4, int d5) {
		return spear(1, d1, d2, d3, d4, d5);
	}

	public static int twos(int d1, int d2, int d3, int d4, int d5) {
		return spear(2, d1, d2, d3, d4, d5);
	}

	public static int threes(int d1, int d2, int d3, int d4, int d5) {
		return spear(3, d1, d2, d3, d4, d5);
	}

	public int fours() {
		return spearInterne(4);
	}

	public int fives() {
		return spearInterne(5);
	}

	public int sixes() {
		return spearInterne(6);
	}
}
