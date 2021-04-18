# ZK-SANRK 示例

## quick run

1. 拉取zksanrk代码

```
git submodule update --init --recursive
```

2. 安装zksnark依赖

ubuntu 18.04及以上：
```
sudo apt install build-essential cmake git libgmp3-dev libprocps-dev python3-markdown libboost-program-options-dev libssl-dev python3 pkg-config
```
其他os：
参考zksnark库[官方文档](https://github.com/scipr-lab/libsnark#build-instructions)

3. 编译

```
mkdir build; cd build; cmake ..; make
```
编译后，会在`build/merkle`下生成`merkle`二进制文件

4. 初始化配置

```
cd ./merkle; ./merkle setup
```

5. 生成证明

```
./merkle prove [data1] [data2] [data3] [data4] [data5] [data6] [data7] [data8] [index]
```
生成后，命令行会输出root的值，copy下来，在验证时使用

6. 验证证明

```
./merkle [root]
```

## 输出示例

初始化配置：

```
$ ./merkle setup
Number of R1CS constraints: 84150
(enter) Call to r1cs_gg_ppzksnark_generator	[             ]	(1618755709.9969s x0.00 from start)
  (enter) Call to r1cs_constraint_system::swap_AB_if_beneficial	[             ]	(1618755710.0116s x0.00 from start)
    (enter) Estimate densities                 	[             ]	(1618755710.0117s x0.00 from start)
      * Non-zero A-count (estimate): 46444
      * Non-zero B-count (estimate): 56373
    (leave) Estimate densities                 	[0.0020s x0.96]	(1618755710.0136s x0.00 from start)
    (enter) Perform the swap                   	[             ]	(1618755710.0137s x0.00 from start)
    (leave) Perform the swap                   	[0.0006s x0.92]	(1618755710.0143s x0.00 from start)
  (leave) Call to r1cs_constraint_system::swap_AB_if_beneficial	[0.0028s x0.89]	(1618755710.0143s x0.00 from start)
  (enter) Call to r1cs_to_qap_instance_map_with_evaluation	[             ]	(1618755710.0144s x0.00 from start)
    (enter) Compute evaluations of A, B, C, H at t	[             ]	(1618755710.0168s x0.00 from start)
    (leave) Compute evaluations of A, B, C, H at t	[0.3002s x0.88]	(1618755710.3170s x0.00 from start)
  (leave) Call to r1cs_to_qap_instance_map_with_evaluation	[0.3027s x0.88]	(1618755710.3171s x0.00 from start)
  * QAP number of variables: 77199
  * QAP pre degree: 84150
  * QAP degree: 98304
  * QAP number of input variables: 256
  (enter) Compute query densities            	[             ]	(1618755710.3173s x0.00 from start)
  (leave) Compute query densities            	[0.0004s x0.89]	(1618755710.3177s x0.00 from start)
  (enter) Compute gamma_ABC for R1CS verification key	[             ]	(1618755710.3177s x0.00 from start)
  (leave) Compute gamma_ABC for R1CS verification key	[0.0001s x0.50]	(1618755710.3178s x0.00 from start)
  (enter) Compute L query for R1CS proving key	[             ]	(1618755710.3179s x0.00 from start)
  (leave) Compute L query for R1CS proving key	[0.0098s x1.00]	(1618755710.3276s x0.00 from start)
  (enter) Generating G1 MSM window table     	[             ]	(1618755710.3308s x0.00 from start)
    Choosing window size 15 for 180016 elements
    * G1 window: 15
  (leave) Generating G1 MSM window table     	[0.4172s x0.98]	(1618755710.7480s x0.00 from start)
  (enter) Generating G2 MSM window table     	[             ]	(1618755710.7481s x0.00 from start)
    Choosing window size 13 for 46444 elements
    * G2 window: 13
  (leave) Generating G2 MSM window table     	[0.5733s x0.98]	(1618755711.3215s x0.00 from start)
  (enter) Generate R1CS proving key          	[             ]	(1618755711.3216s x0.00 from start)
    (enter) Generate queries                   	[             ]	(1618755711.3243s x0.00 from start)
      (enter) Compute the A-query                	[             ]	(1618755711.3243s x0.00 from start)
      ........ DONE!
      (leave) Compute the A-query                	[0.8794s x0.98]	(1618755712.2037s x0.00 from start)
      (enter) Compute the B-query                	[             ]	(1618755712.2038s x0.00 from start)
      Non-zero coordinate count: 46444/77200 (60.16%)
      (leave) Compute the B-query                	[4.1692s x0.99]	(1618755716.3730s x0.00 from start)
      (enter) Compute the H-query                	[             ]	(1618755716.3732s x0.00 from start)
      .......... DONE!
      (leave) Compute the H-query                	[1.5198s x0.98]	(1618755717.8929s x0.00 from start)
      (enter) Compute the L-query                	[             ]	(1618755717.8930s x0.00 from start)
      ........ DONE!
      (leave) Compute the L-query                	[1.1841s x0.98]	(1618755719.0772s x0.00 from start)
    (leave) Generate queries                   	[7.7530s x0.99]	(1618755719.0772s x0.00 from start)
  (leave) Generate R1CS proving key          	[7.7557s x0.99]	(1618755719.0773s x0.00 from start)
  (enter) Generate R1CS verification key     	[             ]	(1618755719.0773s x0.00 from start)
    (enter) Call to alt_bn128_ate_reduced_pairing	[             ]	(1618755719.0774s x0.00 from start)
      (enter) Call to alt_bn128_ate_pairing      	[             ]	(1618755719.0774s x0.00 from start)
        (enter) Call to alt_bn128_ate_precompute_G1	[             ]	(1618755719.0775s x0.00 from start)
        (leave) Call to alt_bn128_ate_precompute_G1	[0.0000s x0.50]	(1618755719.0775s x0.00 from start)
        (enter) Call to alt_bn128_ate_precompute_G2	[             ]	(1618755719.0775s x0.00 from start)
        (leave) Call to alt_bn128_ate_precompute_G2	[0.0004s x0.99]	(1618755719.0779s x0.00 from start)
        (enter) Call to alt_bn128_ate_miller_loop  	[             ]	(1618755719.0779s x0.00 from start)
        (leave) Call to alt_bn128_ate_miller_loop  	[0.0008s x1.00]	(1618755719.0787s x0.00 from start)
      (leave) Call to alt_bn128_ate_pairing      	[0.0012s x0.94]	(1618755719.0787s x0.00 from start)
      (enter) Call to alt_bn128_final_exponentiation	[             ]	(1618755719.0787s x0.00 from start)
        (enter) Call to alt_bn128_final_exponentiation_first_chunk	[             ]	(1618755719.0787s x0.00 from start)
        (leave) Call to alt_bn128_final_exponentiation_first_chunk	[0.0000s x0.91]	(1618755719.0787s x0.00 from start)
        (enter) Call to alt_bn128_final_exponentiation_last_chunk	[             ]	(1618755719.0788s x0.00 from start)
          (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755719.0788s x0.00 from start)
          (leave) Call to alt_bn128_exp_by_neg_z     	[0.0004s x0.99]	(1618755719.0792s x0.00 from start)
          (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755719.0792s x0.00 from start)
          (leave) Call to alt_bn128_exp_by_neg_z     	[0.0004s x0.99]	(1618755719.0796s x0.00 from start)
          (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755719.0796s x0.00 from start)
          (leave) Call to alt_bn128_exp_by_neg_z     	[0.0004s x0.99]	(1618755719.0800s x0.00 from start)
        (leave) Call to alt_bn128_final_exponentiation_last_chunk	[0.0013s x0.98]	(1618755719.0801s x0.00 from start)
      (leave) Call to alt_bn128_final_exponentiation	[0.0014s x0.97]	(1618755719.0801s x0.00 from start)
    (leave) Call to alt_bn128_ate_reduced_pairing	[0.0028s x0.94]	(1618755719.0801s x0.00 from start)
    (enter) Encode gamma_ABC for R1CS verification key	[             ]	(1618755719.0810s x0.00 from start)
      . DONE!
    (leave) Encode gamma_ABC for R1CS verification key	[0.0041s x1.00]	(1618755719.0851s x0.00 from start)
  (leave) Generate R1CS verification key     	[0.0078s x0.97]	(1618755719.0851s x0.00 from start)
(leave) Call to r1cs_gg_ppzksnark_generator	[9.0882s x0.98]	(1618755719.0852s x0.00 from start)
* G1 elements in PK: 329647
* Non-zero G1 elements in PK: 298891
* G2 elements in PK: 77201
* Non-zero G2 elements in PK: 46445
* PK size in bits: 102830126
* G1 elements in VK: 256
* G2 elements in VK: 2
* GT elements in VK: 1
* VK size in bits: 82937
```

生成证明：
```
$ ./merkle prove 1 2 3 4 5 6 7 8 0
0
0
0
0
root is f171e00bb40c83de1f09c64e2cc4558e3c327aa9e8525a467c83576071bc1045
(enter) Call to r1cs_gg_ppzksnark_prover   	[             ]	(1618755775.3051s x0.00 from start)
  (enter) Compute the polynomial H           	[             ]	(1618755775.3052s x0.00 from start)
    (enter) Call to r1cs_to_qap_witness_map    	[             ]	(1618755775.3053s x0.00 from start)
      (enter) Compute evaluation of polynomials A, B on set S	[             ]	(1618755775.3056s x0.00 from start)
      (leave) Compute evaluation of polynomials A, B on set S	[0.0250s x0.81]	(1618755775.3306s x0.00 from start)
      (enter) Compute coefficients of polynomial A	[             ]	(1618755775.3307s x0.00 from start)
      (leave) Compute coefficients of polynomial A	[0.1002s x0.95]	(1618755775.4309s x0.00 from start)
      (enter) Compute coefficients of polynomial B	[             ]	(1618755775.4310s x0.00 from start)
      (leave) Compute coefficients of polynomial B	[0.1008s x0.93]	(1618755775.5318s x0.00 from start)
      (enter) Compute ZK-patch                   	[             ]	(1618755775.5320s x0.00 from start)
      (leave) Compute ZK-patch                   	[0.0072s x0.99]	(1618755775.5392s x0.00 from start)
      (enter) Compute evaluation of polynomial A on set T	[             ]	(1618755775.5392s x0.00 from start)
      (leave) Compute evaluation of polynomial A on set T	[0.1027s x0.93]	(1618755775.6419s x0.00 from start)
      (enter) Compute evaluation of polynomial B on set T	[             ]	(1618755775.6420s x0.00 from start)
      (leave) Compute evaluation of polynomial B on set T	[0.1032s x0.92]	(1618755775.7452s x0.00 from start)
      (enter) Compute evaluation of polynomial H on set T	[             ]	(1618755775.7453s x0.00 from start)
        (enter) Compute evaluation of polynomial C on set S	[             ]	(1618755775.7490s x0.00 from start)
        (leave) Compute evaluation of polynomial C on set S	[0.0145s x0.78]	(1618755775.7634s x0.00 from start)
        (enter) Compute coefficients of polynomial C	[             ]	(1618755775.7635s x0.00 from start)
        (leave) Compute coefficients of polynomial C	[0.1023s x0.94]	(1618755775.8658s x0.00 from start)
        (enter) Compute evaluation of polynomial C on set T	[             ]	(1618755775.8660s x0.00 from start)
        (leave) Compute evaluation of polynomial C on set T	[0.1028s x0.92]	(1618755775.9688s x0.00 from start)
        (enter) Divide by Z on set T               	[             ]	(1618755775.9703s x0.00 from start)
        (leave) Divide by Z on set T               	[0.0798s x0.90]	(1618755776.0501s x0.00 from start)
      (leave) Compute evaluation of polynomial H on set T	[0.3049s x0.92]	(1618755776.0502s x0.00 from start)
      (enter) Compute coefficients of polynomial H	[             ]	(1618755776.0503s x0.00 from start)
      (leave) Compute coefficients of polynomial H	[0.1111s x0.93]	(1618755776.1614s x0.00 from start)
      (enter) Compute sum of H and ZK-patch      	[             ]	(1618755776.1615s x0.00 from start)
      (leave) Compute sum of H and ZK-patch      	[0.0007s x0.94]	(1618755776.1622s x0.00 from start)
    (leave) Call to r1cs_to_qap_witness_map    	[0.8570s x0.92]	(1618755776.1623s x0.00 from start)
  (leave) Compute the polynomial H           	[0.8574s x0.92]	(1618755776.1626s x0.00 from start)
  (enter) Compute the proof                  	[             ]	(1618755776.1627s x0.00 from start)
    (enter) Compute evaluation to A-query      	[             ]	(1618755776.1628s x0.00 from start)
    (enter) Process scalar vector              	[             ]	(1618755776.1631s x0.00 from start)
      * Elements of w skipped: 37330 (48.35%)
      * Elements of w processed with special addition: 37274 (48.28%)
      * Elements of w remaining: 2596 (3.36%)
    (leave) Process scalar vector              	[0.0283s x0.75]	(1618755776.1914s x0.00 from start)
    (leave) Compute evaluation to A-query      	[0.0366s x0.81]	(1618755776.1994s x0.00 from start)
    (enter) Compute evaluation to B-query      	[             ]	(1618755776.1995s x0.00 from start)
    (enter) Process scalar vector              	[             ]	(1618755776.1995s x0.00 from start)
      * Elements of w skipped: 23258 (50.08%)
      * Elements of w processed with special addition: 23186 (49.92%)
      * Elements of w remaining: 0 (0.00%)
    (leave) Process scalar vector              	[0.1079s x0.93]	(1618755776.3074s x0.00 from start)
    (leave) Compute evaluation to B-query      	[0.1080s x0.93]	(1618755776.3075s x0.00 from start)
    (enter) Compute evaluation to H-query      	[             ]	(1618755776.3075s x0.00 from start)
    (leave) Compute evaluation to H-query      	[1.6896s x0.99]	(1618755777.9972s x0.00 from start)
    (enter) Compute evaluation to L-query      	[             ]	(1618755777.9973s x0.00 from start)
    (enter) Process scalar vector              	[             ]	(1618755777.9973s x0.00 from start)
      * Elements of w skipped: 37191 (48.34%)
      * Elements of w processed with special addition: 37156 (48.29%)
      * Elements of w remaining: 2596 (3.37%)
    (leave) Process scalar vector              	[0.0344s x0.82]	(1618755778.0318s x0.00 from start)
    (leave) Compute evaluation to L-query      	[0.0537s x0.86]	(1618755778.0509s x0.00 from start)
  (leave) Compute the proof                  	[1.8902s x0.98]	(1618755778.0529s x0.00 from start)
(leave) Call to r1cs_gg_ppzksnark_prover   	[2.7479s x0.96]	(1618755778.0530s x0.00 from start)
* G1 elements in proof: 2
* G2 elements in proof: 1
* Proof size in bits: 1019
Proof generated!
```

验证证明：

```
$ ./merkle verify f171e00bb40c83de1f09c64e2cc4558e3c327aa9e8525a467c83576071bc1045
(enter) Call to r1cs_gg_ppzksnark_verifier_strong_IC	[             ]	(1618755804.0365s x0.00 from start)
  (enter) Call to r1cs_gg_ppzksnark_verifier_process_vk	[             ]	(1618755804.0365s x0.00 from start)
    (enter) Call to alt_bn128_ate_precompute_G2	[             ]	(1618755804.0366s x0.00 from start)
    (leave) Call to alt_bn128_ate_precompute_G2	[0.0004s x0.89]	(1618755804.0370s x0.00 from start)
    (enter) Call to alt_bn128_ate_precompute_G2	[             ]	(1618755804.0371s x0.00 from start)
    (leave) Call to alt_bn128_ate_precompute_G2	[0.0004s x0.88]	(1618755804.0374s x0.00 from start)
  (leave) Call to r1cs_gg_ppzksnark_verifier_process_vk	[0.0009s x0.75]	(1618755804.0375s x0.00 from start)
  (enter) Call to r1cs_gg_ppzksnark_online_verifier_strong_IC	[             ]	(1618755804.0375s x0.00 from start)
    (enter) Call to r1cs_gg_ppzksnark_online_verifier_weak_IC	[             ]	(1618755804.0376s x0.00 from start)
      (enter) Accumulate input                   	[             ]	(1618755804.0376s x0.00 from start)
      (leave) Accumulate input                   	[0.0002s x0.75]	(1618755804.0378s x0.00 from start)
      (enter) Check if the proof is well-formed  	[             ]	(1618755804.0379s x0.00 from start)
      (leave) Check if the proof is well-formed  	[0.0005s x0.04]	(1618755804.0383s x0.00 from start)
      (enter) Online pairing computations        	[             ]	(1618755804.0384s x0.00 from start)
        (enter) Check QAP divisibility             	[             ]	(1618755804.0384s x0.00 from start)
          (enter) Call to alt_bn128_ate_precompute_G1	[             ]	(1618755804.0385s x0.00 from start)
          (leave) Call to alt_bn128_ate_precompute_G1	[0.0001s x0.24]	(1618755804.0386s x0.00 from start)
          (enter) Call to alt_bn128_ate_precompute_G2	[             ]	(1618755804.0386s x0.00 from start)
          (leave) Call to alt_bn128_ate_precompute_G2	[0.0004s x0.90]	(1618755804.0390s x0.00 from start)
          (enter) Call to alt_bn128_ate_precompute_G1	[             ]	(1618755804.0391s x0.00 from start)
          (leave) Call to alt_bn128_ate_precompute_G1	[0.0001s x0.22]	(1618755804.0391s x0.00 from start)
          (enter) Call to alt_bn128_ate_precompute_G1	[             ]	(1618755804.0392s x0.00 from start)
          (leave) Call to alt_bn128_ate_precompute_G1	[0.0001s x0.21]	(1618755804.0393s x0.00 from start)
          (enter) Call to alt_bn128_ate_miller_loop  	[             ]	(1618755804.0393s x0.00 from start)
          (leave) Call to alt_bn128_ate_miller_loop  	[0.0009s x0.91]	(1618755804.0402s x0.00 from start)
          (enter) Call to alt_bn128_ate_double_miller_loop	[             ]	(1618755804.0403s x0.00 from start)
          (leave) Call to alt_bn128_ate_double_miller_loop	[0.0013s x0.95]	(1618755804.0415s x0.00 from start)
          (enter) Call to alt_bn128_final_exponentiation	[             ]	(1618755804.0416s x0.00 from start)
            (enter) Call to alt_bn128_final_exponentiation_first_chunk	[             ]	(1618755804.0417s x0.00 from start)
            (leave) Call to alt_bn128_final_exponentiation_first_chunk	[0.0001s x0.44]	(1618755804.0418s x0.00 from start)
            (enter) Call to alt_bn128_final_exponentiation_last_chunk	[             ]	(1618755804.0453s x0.00 from start)
              (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755804.0454s x0.00 from start)
              (leave) Call to alt_bn128_exp_by_neg_z     	[0.0005s x0.91]	(1618755804.0458s x0.00 from start)
              (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755804.0460s x0.00 from start)
              (leave) Call to alt_bn128_exp_by_neg_z     	[0.0005s x0.91]	(1618755804.0465s x0.00 from start)
              (enter) Call to alt_bn128_exp_by_neg_z     	[             ]	(1618755804.0465s x0.00 from start)
              (leave) Call to alt_bn128_exp_by_neg_z     	[0.0005s x0.91]	(1618755804.0470s x0.00 from start)
            (leave) Call to alt_bn128_final_exponentiation_last_chunk	[0.0018s x0.79]	(1618755804.0471s x0.00 from start)
          (leave) Call to alt_bn128_final_exponentiation	[0.0055s x0.27]	(1618755804.0472s x0.00 from start)
        (leave) Check QAP divisibility             	[0.0088s x0.46]	(1618755804.0472s x0.00 from start)
      (leave) Online pairing computations        	[0.0089s x0.46]	(1618755804.0473s x0.00 from start)
    (leave) Call to r1cs_gg_ppzksnark_online_verifier_weak_IC	[0.0097s x0.44]	(1618755804.0473s x0.00 from start)
  (leave) Call to r1cs_gg_ppzksnark_online_verifier_strong_IC	[0.0099s x0.43]	(1618755804.0474s x0.00 from start)
(leave) Call to r1cs_gg_ppzksnark_verifier_strong_IC	[0.0110s x0.46]	(1618755804.0474s x0.00 from start)
Verification pass!
```
