# JavaLayersCode-ML
Layers Code in Java - ML


import java.util.Scanner;


		class NeuralNetwork {
		    private int numLayers;
		    private int[] numNodes;
		    private double[][][] weights;

		    public NeuralNetwork(int numLayers, int[] numNodes) {
		        this.numLayers = numLayers;
		        this.numNodes = numNodes;
		        weights = new double[numLayers - 1][][];
		        for (int i = 0; i < numLayers - 1; i++) {
		            weights[i] = new double[numNodes[i]][numNodes[i + 1]];
		        }
		    }

		    public void setWeights() {
		        Scanner scanner = new Scanner(System.in);
		        for (int i = 0; i < numLayers - 1; i++) {
		            System.out.println("Enter weights for connections between layer " + (i + 1) + " and layer " + (i + 2) + ":");
		            for (int j = 0; j < numNodes[i]; j++) {
		                for (int k = 0; k < numNodes[i + 1]; k++) {
		                    System.out.print("Weight from node " + (j + 1) + " to node " + (k + 1) + ": ");
		                    weights[i][j][k] = scanner.nextDouble();
		                }
		            }
		        }
		    }

		    public double getWeight(int fromNode, int toNode) {
                // Assuming nodes are 1-indexed
                return weights[fromNode - 1][fromNode - 1][toNode - 1];
            }

		    public static void main(String[] args) {
                Scanner scanner = new Scanner(System.in);
        
                System.out.print("Enter the number of layers: ");
                int numLayers = scanner.nextInt();
        
                int[] numNodes = new int[numLayers];
                for (int i = 0; i < numLayers; i++) {
                    System.out.print("Enter the number of nodes in layer " + (i + 1) + ": ");
                    numNodes[i] = scanner.nextInt();
                }
        
                NeuralNetwork neuralNetwork = new NeuralNetwork(numLayers, numNodes);
                neuralNetwork.setWeights();
        
                // Example: querying weight of an edge
                System.out.print("Enter the node in the first layer: ");
                int fromNode = scanner.nextInt();
                System.out.print("Enter the node in the next layer: ");
                int toNode = scanner.nextInt();
                System.out.println("Weight from node " + fromNode + " to node " + toNode + ": " + neuralNetwork.getWeight(fromNode, toNode));
            }
        }
