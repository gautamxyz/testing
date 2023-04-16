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
										git.listRemote(['--heads', remote], function (err, remoteRefs) {
											if (err) {
												vscode.window.showErrorMessage(err);
											} else if (!remoteRefs.includes('refs/heads/dev')) {
												vscode.window.showErrorMessage('The dev branch does not exist in the remote repository.');
											} else {
												git.mergeFromTo('dev', 'testing', function (err, mergeSummary) {
													// rest of the code
													if (err) {
														console.log("here 3 ", err)
														vscode.window.showErrorMessage(err);
													}
													else {
														git.push(remote, 'testing', function (err) {
															if (err) {
																console.log("here 4 ", err)
																vscode.window.showErrorMessage(err);
															}
															else {
																vscode.window.showInformationMessage('Pushed successfully');
															}
														});
													}
												});
											}
										});
									}
								})
							}
						})