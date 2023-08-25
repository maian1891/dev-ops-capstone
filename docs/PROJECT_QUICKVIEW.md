# Udacity - Cloud DevOps Engineer - Capstone - Project quick view

1. The project uses a centralized image repository to manage images built in the project. After a clean build, images are pushed to the repository.
<img src="images/build_push_image_docker.png" />

2. Code is checked against a linter as part of a Continuous Integration step (demonstrated w/ two screenshots)
<img src="images/check_lint_test_app_failed.png" />
<img src="images/check_lint_success.png" />

3. The project takes a Dockerfile and creates a Docker container in the pipeline.
<img src="images/build_app_image.png" />
<img src="images/push_app_image.png" />

4. The cluster is deployed with CloudFormation or Ansible. This should be in the source code of the student’s submission.
<img src="images/aws_cloudformation_network_stack.png" />
<img src="images/aws_cloudformation_cluster_stack.png" />

5. The project performs the correct steps to do a blue/green or rolling deployment into the environment selected. Submit the following screenshots as evidence of the successful completion of chosen deployment methodology:
    1. Screenshot of the Circle CI or Jenkins pipeline showing all stages passed successfully.
    <img src="images/circleci_full_success_pipeline.png" />

    2. Screenshot of your AWS EC2 page showing the newly created (for blue/green) or modified (for rolling) instances running as the EKS cluster nodes.
    <img src="images/ec2-instances.png" />
    <img src="images/eks-cluster.png" />
    <img src="images/eks_kubectl_get_nodes.png" />
    <img src="images/rolling_success.png" />
    
   