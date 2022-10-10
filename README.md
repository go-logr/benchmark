# Benchmark of logr implementations

## Implementations

- **a function** (can bridge to non-structured libraries): [funcr](https://github.com/go-logr/logr/tree/master/funcr)
- **log** (the Go standard library logger): [stdr](https://github.com/go-logr/stdr)
- **github.com/google/glog**: [glogr](https://github.com/go-logr/glogr)
- **github.com/sirupsen/logrus**: [logrusr](https://github.com/bombsimon/logrusr)
- **go.uber.org/zap**: [zapr](https://github.com/go-logr/zapr)
- **github.com/rs/zerolog**: [zerologr](https://github.com/go-logr/zerologr)
- **k8s.io/klog/v2**: [klogr](https://github.com/kubernetes/klog/tree/main/klogr)

## Benchmark

Lastest benchmark in [Github Action](https://github.com/go-logr/benchmark/actions/workflows/test.yaml)

```
2022-02-07

goos: linux
goarch: amd64
pkg: benchmark
cpu: Intel(R) Xeon(R) Platinum 8272CL CPU @ 2.60GHz

BenchmarkDiscardInfoOneArg-2         	29582142	        39.83 ns/op	      32 B/op	       1 allocs/op
BenchmarkDiscardInfoSeveralArgs-2    	12446994	        93.78 ns/op	     176 B/op	       2 allocs/op
BenchmarkDiscardV0Info-2             	12744861	        95.27 ns/op	     176 B/op	       2 allocs/op
BenchmarkDiscardV9Info-2             	12594637	        93.64 ns/op	     176 B/op	       2 allocs/op
BenchmarkDiscardError-2              	10781566	       104.0 ns/op	     176 B/op	       2 allocs/op
BenchmarkDiscardWithValues-2         	25914538	        47.78 ns/op	      64 B/op	       1 allocs/op
BenchmarkDiscardWithName-2           	363818114	         3.292 ns/op	       0 B/op	       0 allocs/op
BenchmarkDiscardWithCallDepth-2      	100000000	        10.68 ns/op	       0 B/op	       0 allocs/op

BenchmarkFuncrInfoOneArg-2           	 1318761	       904.0 ns/op	    1152 B/op	       7 allocs/op
BenchmarkFuncrInfoSeveralArgs-2      	  604104	      1998 ns/op	    1448 B/op	      17 allocs/op
BenchmarkFuncrV0Info-2               	  601426	      2000 ns/op	    1448 B/op	      17 allocs/op
BenchmarkFuncrV9Info-2               	11611688	       104.5 ns/op	     176 B/op	       2 allocs/op
BenchmarkFuncrError-2                	  561898	      2175 ns/op	    1480 B/op	      19 allocs/op
BenchmarkFuncrWithValues-2           	 1686696	       660.2 ns/op	     328 B/op	       8 allocs/op
BenchmarkFuncrWithName-2             	14652040	        82.81 ns/op	     160 B/op	       1 allocs/op
BenchmarkFuncrWithCallDepth-2        	14472902	        83.26 ns/op	     160 B/op	       1 allocs/op

BenchmarkStdrInfoOneArg-2            	  697104	      1752 ns/op	    1200 B/op	       8 allocs/op
BenchmarkStdrInfoSeveralArgs-2       	  399481	      2885 ns/op	    1496 B/op	      18 allocs/op
BenchmarkStdrV0Info-2                	  417754	      2877 ns/op	    1496 B/op	      18 allocs/op
BenchmarkStdrV9Info-2                	12667026	        95.66 ns/op	     176 B/op	       2 allocs/op
BenchmarkStdrError-2                 	  400686	      3031 ns/op	    1528 B/op	      20 allocs/op
BenchmarkStdrWithValues-2            	 1852478	       643.4 ns/op	     328 B/op	       8 allocs/op
BenchmarkStdrWithName-2              	14957589	        81.70 ns/op	     160 B/op	       1 allocs/op
BenchmarkStdrWithCallDepth-2         	14793274	        82.72 ns/op	     160 B/op	       1 allocs/op

BenchmarkGlogrInfoOneArg-2           	  379180	      3172 ns/op	    1424 B/op	      11 allocs/op
BenchmarkGlogrInfoSeveralArgs-2      	  276160	      4355 ns/op	    1720 B/op	      21 allocs/op
BenchmarkGlogrV0Info-2               	  270379	      4511 ns/op	    1720 B/op	      21 allocs/op
BenchmarkGlogrV9Info-2               	12271572	        98.11 ns/op	     176 B/op	       2 allocs/op
BenchmarkGlogrError-2                	  269508	      4503 ns/op	    1752 B/op	      23 allocs/op
BenchmarkGlogrWithValues-2           	 1821219	       663.4 ns/op	     312 B/op	       8 allocs/op
BenchmarkGlogrWithName-2             	14607142	        83.01 ns/op	     144 B/op	       1 allocs/op
BenchmarkGlogrWithCallDepth-2        	14942923	        80.98 ns/op	     144 B/op	       1 allocs/op

BenchmarkLogrusrInfoOneArg-2         	  240513	      5025 ns/op	    1752 B/op	      28 allocs/op
BenchmarkLogrusrInfoSeveralArgs-2    	  161313	      7400 ns/op	    2088 B/op	      35 allocs/op
BenchmarkLogrusrV0Info-2             	  164017	      7333 ns/op	    2088 B/op	      35 allocs/op
BenchmarkLogrusrV9Info-2             	12288049	        96.73 ns/op	     176 B/op	       2 allocs/op
BenchmarkLogrusrError-2              	  137755	      8793 ns/op	    2624 B/op	      41 allocs/op
BenchmarkLogrusrWithValues-2         	 1559294	       760.9 ns/op	     960 B/op	       8 allocs/op
BenchmarkLogrusrWithName-2           	 2101682	       570.6 ns/op	     592 B/op	       7 allocs/op
BenchmarkLogrusrWithCallDepth-2      	17443572	        69.27 ns/op	      64 B/op	       1 allocs/op

BenchmarkZaprInfoOneArg-2            	  204626	      5935 ns/op	     712 B/op	      15 allocs/op
BenchmarkZaprInfoSeveralArgs-2       	  168010	      7119 ns/op	    1192 B/op	      17 allocs/op
BenchmarkZaprV0Info-2                	  166699	      7191 ns/op	    1192 B/op	      17 allocs/op
BenchmarkZaprV9Info-2                	11474546	       104.1 ns/op	     176 B/op	       2 allocs/op
BenchmarkZaprError-2                 	  167481	      7264 ns/op	    1320 B/op	      18 allocs/op
BenchmarkZaprWithValues-2            	 1212664	       993.1 ns/op	    1488 B/op	       8 allocs/op
BenchmarkZaprWithName-2              	11181411	       107.3 ns/op	     144 B/op	       2 allocs/op
BenchmarkZaprWithCallDepth-2         	 8214675	       146.8 ns/op	     160 B/op	       3 allocs/op

BenchmarkZerologrInfoOneArg-2        	  596510	      2010 ns/op	     176 B/op	       4 allocs/op
BenchmarkZerologrInfoSeveralArgs-2   	  445365	      2735 ns/op	     336 B/op	       6 allocs/op
BenchmarkZerologrV0Info-2            	  438519	      2765 ns/op	     336 B/op	       6 allocs/op
BenchmarkZerologrV9Info-2            	12310707	        95.97 ns/op	     176 B/op	       2 allocs/op
BenchmarkZerologrError-2             	  439524	      2767 ns/op	     336 B/op	       6 allocs/op
BenchmarkZerologrWithValues-2        	 3002196	       399.0 ns/op	     704 B/op	       4 allocs/op
BenchmarkZerologrWithName-2          	28722273	        42.01 ns/op	      32 B/op	       1 allocs/op
BenchmarkZerologrWithCallDepth-2     	20906972	        56.97 ns/op	      32 B/op	       1 allocs/op
```
