# testing
This repo is for testing purposes only. We are testing dev branch, testing for merge.

Here

git.fetch(remote, 'testing', function (err) {
								if (err) {
									console.log("here 1 ", err)
									vscode.window.showErrorMessage(err);
								}
								else {
									console.log("here 1 ")
									git.checkout('testing', function (err) {
										if (err) {
											console.log("here 2 ", err)
											vscode.window.showErrorMessage(err);
										}
										else {
											console.log("here 2 ")
											git.mergeFromTo(remote, 'dev', function (err) {
												if (err) {
													console.log("here 3 ", err)
													vscode.window.showErrorMessage(err);
												}
												else {
													console.log("here 3 ")
													git.push(remote, 'testing', function (err) {
														if (err) {
															console.log("here 4 ", err)
															vscode.window.showErrorMessage(err);
														}
														else {
															console.log("here 4 ")
															vscode.window.showInformationMessage('Pushed successfully');
														}
													})
												}
											})
										}
									})
								}
							})
